---
title: "How do I reinstall grub using super grub?"
date: 2008-03-01
forum: General Help
---

### Post by Roasted on 2008-03-01
I have super grub on disk. When booting to it, I really have no idea what I am doing, however Ubuntu is bootable w/ super grub, but without it I get error 22. When trying to boot windows without grub, I get error 13.

I work long hours so my time available to tinker with this is really diminished to a matter of minutes per day, hence why I'm posting here hoping to check back later/tomorrow with a sure-fire response on what to do.

I've googled for a how-to guide but most of them just boast about the abilities of super grub and don't actually have a step by step guide for actually using the darn thing.

What can I do?

Oh just for the record. I had a successful dual boot with Gutsy and XP Pro. I reinstalled Gutsy due to insane lag problems the OS was displaying. I even posted here and nobody was completely sure what was going on, so I decided to do a fresh install since I had a lot of garbage settings on it and stuff. That's where I had these issues.

---

### Post by confused57 on 2008-03-01
> **Roasted said:**
> I have super grub on disk. When booting to it, I really have no idea what I am doing, however Ubuntu is bootable w/ super grub, but without it I get error 22. When trying to boot windows without grub, I get error 13.

I work long hours so my time available to tinker with this is really diminished to a matter of minutes per day, hence why I'm posting here hoping to check back later/tomorrow with a sure-fire response on what to do.

I've googled for a how-to guide but most of them just boast about the abilities of super grub and don't actually have a step by step guide for actually using the darn thing.

What can I do?

Oh just for the record. I had a successful dual boot with Gutsy and XP Pro. I reinstalled Gutsy due to insane lag problems the OS was displaying. I even posted here and nobody was completely sure what was going on, so I decided to do a fresh install since I had a lot of garbage settings on it and stuff. That's where I had these issues.
Here are grub errors & possible solutions:
[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors)

You can also use the Ubuntu live cd to install grub's IPL(Initial Program Loader) to the mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Have you seen this site for SGD instructions?:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Should be something like:
Super Grub Disk(No Help)
English SGD
Linux
Fix Boot of Linux(or something to that effect)

If none of the above works, you could boot into Ubuntu using SGD and post the output of:
```
sudo fdisk -l
```
-l is a small "L"
and
```
gedit /boot/grub/menu.lst
```
just posting the boot entries should be sufficient

---

### Post by Roasted on 2008-03-01
I did the 2nd link where it says to find/boot/grub/stage1 and all of that. Didn't work. Still got the same error 22 when trying to boot to ubuntu.

Here's my fdisk -l output.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa74ba74b

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       24792   199141708+  83  Linux

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        3948      996030   82  Linux swap / Solaris
/dev/sda3            3949        5772    14651280   83  Linux
/dev/sda4            5773       30515   198748147+  83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43e0877d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          62      497983+   5  Extended
/dev/sdb2              63       30515   244613722+  83  Linux
/dev/sdb5               1          62      497952   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


I went to gedit /boot/grub/menu.lst and it was empty.

---

### Post by confused57 on 2008-03-01
If you're booted into Ubuntu, open a terminal:
```
cd /boot/grub
ls -la
```
copy & paste the commands & note if you have a menu.lst file & a device.map file

You could also do this from Nautilus, navigate to your /boot directory, etc.

Added:  Did "find /boot/grub/stage1" show the root partition?  I'm wondering if somehow your new Gutsy installed grub to a different hard drive's mbr and you're booting to the mbr of a different hard drive where your old Gutsy installed grub?

---

### Post by Roasted on 2008-03-01
It said hd1,2, so I put hd1,2 in and it seemed to work.

I have 3 hard drives in my computer, however only 1 has any operating systems on it. The other 2 are simply backups.

In the past I've disconnected the drives when installing linux for sake of being consistent with where I install stuff. But that's bogus to have to disconnect drives to install an OS. I don't see why other drives being present would pose a hinderence.

---

### Post by confused57 on 2008-03-02
> **Roasted said:**
> It said hd1,2, so I put hd1,2 in and it seemed to work.

I have 3 hard drives in my computer, however only 1 has any operating systems on it. The other 2 are simply backups.

In the past I've disconnected the drives when installing linux for sake of being consistent with where I install stuff. But that's bogus to have to disconnect drives to install an OS. I don't see why other drives being present would pose a hinderence.
When there is a mixture of IDE & SATA, grub usually recognizes the IDE drive as (hd0), instead of the SATA drive where you installed Ubuntu, even if it's selected as the first hard drive in bios.  It's definitely a shortcoming of grub presently.
   What you can do is boot the Ubuntu live cd:
```
sudo grub
root (hd1,2)
setup (hd1)
quit
```

Boot first to your SATA(?) drive with Ubuntu installed, highlight your Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd1,2) to (hd0,2), press "enter", then "b" to boot.
This is temporary, but you can make it permanent in your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
you'll also need to change the line with #groot to (hd0,2)...leave the # in front of groot.

You'll also need to change the Windows root to (hd0,0) and remove any map lines if present.

---

### Post by Roasted on 2008-03-02
I did exactly what you said, but my menu.lst is completely blank.

Should I just unhook the drives and reinstall?

---

### Post by confused57 on 2008-03-02
> **Roasted said:**
> I did exactly what you said, but my menu.lst is completely blank.

Should I just unhook the drives and reinstall?
I'm not sure why your menu.lst is not showing anything.  Disconnecting your drives would probably be the way to be sure grub is installed to the mbr of the drive with Ubuntu; however, if you want to try with your drives connected, near the end of the installation, click the "Advanced" button in the lower right of the screen...type in /dev/sda(if this is how your Ubuntu drive is recognized by the installer) in place of the default (hd0), which is probably your IDE drive to grub.

If you reinstall with your drives connected, you'll need to use the "e"(edit) method as I described in my previous reply to boot Ubuntu.  If it works then you can make the changes permanent in your /boot/grub/menu.lst.

---

### Post by Roasted on 2008-03-04
I just got fed up and did a fresh install with only my operating system hard drive connected. I disconnected my SATA and IDE backup drives. Everything works like a charm... installing google earth as I type this. :)

---

### Post by confused57 on 2008-03-04
> **Roasted said:**
> I just got fed up and did a fresh install with only my operating system hard drive connected. I disconnected my SATA and IDE backup drives. Everything works like a charm... installing google earth as I type this. :)
Thanks for the update...know it was a pain in the ***, but probably the best way to assure a working installation & dualboot.

---

### Post by xen-uno on 2008-03-04
Opposite for me (or maybe not ... I've been drinking) ... Grub incorrectly used boot parameters of hd(3,2) (or maybe 2,3 which is definitely SATA ... 3rd in boot order) on my setup. First 2 drives are IDE as well as the last (4 hd's total). XP was on (0,0) and Ub installed on (1,2). The alt install must have put Grub on (3,2) as well which is a partitionless drive last in the drive order, and SuperGrub got it wrong too but at least I was able to edit it and get in, then correct.

---

