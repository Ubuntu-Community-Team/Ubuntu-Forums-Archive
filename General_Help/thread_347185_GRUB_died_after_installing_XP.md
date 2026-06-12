---
title: "GRUB died after installing XP"
date: 2007-01-26
forum: General Help
---

### Post by calford on 2007-01-26
Hi,
I had windows 2000 + ubuntu working fine in 2 HDD (2000 in SATA and Linux on IDE).
i had to install XP and now my GRUB is gone. I guess it was on my MBR.

How do i get it back without having to install Ubuntu again?

Thanks

---

### Post by meng on 2007-01-26
Yes Windows overwrites the MBR, so grub has been overwritten. It's a common problem that can't be prevented but is easily fixed.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by calford on 2007-01-26
Thanks for your reply meng
I tried what it says in the link but got the following error message

grub> root (hd0,0)

Error 21: Selected disk does not exist

grub> setup (hd0)

Error 12: Invalid device requested

i used an ubuntu live cd

---

### Post by Monkalou on 2007-01-26
Are you sure you used sudo?  Those (somewhat confusing) errors can come up if you don't.

---

### Post by calford on 2007-01-26
Yes,
just tried again 
sudo grub

and then i got the same errors
grub> root (hd0,0)

Error 21: Selected disk does not exist

grub> setup (hd0)

Error 12: Invalid device requested

---

### Post by calford on 2007-01-27
just tried sudo -i and got this message

ubuntu@ubuntu:~$ sudo -i grub
/sbin/grub: /sbin/grub: cannot execute binary file

---

### Post by foxmulder881 on 2007-01-27
You'd be suprised how many people do this accidentally. ALWAYS remember to install Windows first.

---

### Post by calford on 2007-01-27
ok, i managed to get the GRUB menu running, but now neither ubuntu nor windows boot

this is what i get when i select linux to boot:

booting 'ubuntu, kernel; 2.6.15-17-386'
root (hd1,0)
Error 18: selected cylinder exceeds maximum supported by BIOS

if i choose windows it goes back to the GRUB menu.

when i was configuring GRUB i set it up as root (hd0,0) dont know if that helps


thanks

---

### Post by ~LoKe on 2007-01-27
It really depends on how your partitions are set up.  I would suggest throwing in a LiveCD and booting off that.  Once you're up to the desktop, open a terminal and do the following:
```
sudo fdisk -l
```
It should list all your disks.  Look for the one that would be your root.  It might be something like /dev/sda1, /dev/hda1, etc.
Once you've located it (and I'll assume it was /dev/hda1), do the following:
```
sudo mkdir /mnt/root
```
```
sudo mount /dev/hda1 /mnt/root
```
```
sudo chroot /mnt/root/ su
```

Now you have complete control over your old system.  It would be easier now to try and fix the problem.
```
sudo grub-update
```

Then again, it would be best if you could tell us which partition you're booting from, because that's what the hd(x,x) means.  Check if you have a backup file or something similar:
```
ls /boot/grub|grep menu
```
If you do, you could open it up and check out how that one's set up, look for the hd(x,x) lines and use those values.

---

### Post by calford on 2007-01-27
thanks a lot ~loke

this is my menu.lst

title		Ubuntu, kernel 2.6.15-27-386

root		(hd1,0)

kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sdb1 ro quiet splash

initrd		/boot/initrd.img-2.6.15-27-386

savedefault

boot



# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda1

title		Microsoft Windows 2000 Professional

root		(hd0,0)

savedefault

makeactive

chainloader	+1

and this is my device.map under the same root/boot/grub folder on my old system

(hd0)	/dev/sda
(hd1)	/dev/sdb

this is the result of fdisk -l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6489    52122861    7  HPFS/NTFS
/dev/sda2            6490       24321   143235540    f  W95 Ext'd (LBA)
/dev/sda5            6490       19354   103338081    7  HPFS/NTFS
/dev/sda6           19355       24321    39897396    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40017485312 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4663    37455516   83  Linux
/dev/sdb2            4664        4865     1622565    5  Extended
/dev/sdb5            4664        4865     1622533+  82  Linux swap / Solaris

i want to have GRUB on my linux disk (sdb)

when i used sudo grub-update i got this
root@ubuntu:/# sudo grub-update
sudo: unable to lookup ubuntu via gethostbyname()

thanks a lot

---

