---
title: "cant recover GRUB after XP install - FAQ tried"
date: 2008-06-12
forum: General Help
---

### Post by cernoch on 2008-06-12
very short introduction: I reinstalled XP on my dual boot computer, without formating the c: drive. Boot loader got lost, computer is booting straight to XP. 
Happened to me before, so I googled and tried pretty much all methods suggested here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
but to no avail.

eg:
```

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,5)
 (hd1,4)

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

grub> 
```

These screencaps look like bad news to me, dont they? first is how XP shows partitions on /dev/sda (which is 320GB drive, not 566GB as XP states; there is no free space) the attachment is linux installer:
[IMG]http://www.bikeguide.org/forums/attachment.php?attachmentid=89821&d=1213279200[/IMG]


Can anyone help?

---

### Post by Ender305 on 2008-06-12
it looks like hd1 is the hard drive you want to set up GRUB on, not hd0, since (hd0,5) would be the sixth partition on the disk and on sdb, thats the swap partiton, but (hd1,4) is the fifth partition on sdb, which is ext3, so you want to run "setup (hd1)" not (hd0)

---

### Post by cernoch on 2008-06-12
this should help explain it little better. I really want to reinstall it on sda

sdb is drive from my old computer, I didnt get to formating it yet

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdeaedeae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       38912   292077765    f  W95 Ext'd (LBA)
/dev/sda3            3826       38912   281836296    7  HPFS/NTFS
/dev/sda5            2551        3644     8787492   83  Linux
/dev/sda6            3645        3825     1453851   82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1044     8385898+   7  HPFS/NTFS
/dev/sdb2            1045       24791   190747777+   f  W95 Ext'd (LBA)
/dev/sdb5   *        1045        1762     5767272   83  Linux
/dev/sdb6            1763        1827      522081   82  Linux swap / Solaris
/dev/sdb7            1828        6004    33551721    b  W95 FAT32
/dev/sdb8            6005       24791   150906546    7  HPFS/NTFS

```

---

### Post by meierfra. on 2008-06-12
> omitting empty partition (5) 

I think this is you problem.  Grub is getting confused. According to "find /boot/grub/stage1" your ubuntu partition is "(hd0,5)". Since grub starts counting at zero, that translates into "/dev/sda6". But according to "fdisk" your ubuntu partition is "/dev/sda5".

Testdisk (see my signature) might be able to fix your partition table.

---

### Post by heatblazer on 2008-06-13
Privat Oblasti? Hey, dude, are you from the Balkans? Hello from Bulgaria, mate. I am rooting for the fix of your boot. Have you tried to boot a Live CD and install the GRUB again? 


If you run a dual-boot system with Linux and Windows, this has happened to you. You had to do your monthly reinstall of Windows, and now you don't see the linux bootloader anymore, so you can't boot into Ubuntu or whatever flavor of linux you prefer.

Here's the quick and easy way to re-enable Grub.

1) Boot off the LiveCD

2) Open a Terminal and type in the following commands, noting that the first command will put you into the grub "prompt", and the next 3 commands will be executed there. Also note that hd0,0 implies the first hard drive and the first partition on that drive, which is where you probably installed grub to during installation. If not, then adjust accordingly.

    sudo grub

    > root (hd0,0)

    > setup (hd0)

    > exit

Reboot (removing the livecd), and your boot menu should be back.

 

Only read below if Windows is now missing from the boot menu

If you installed Ubuntu before you installed Windows, then Ubuntu will not have anything in the grub configuration for Windows. This is where you'll have to do a bit of manual editing to the grub boot menu file.

If you open the file /boot/grub/menu.lst with the following command:

    sudo gedit /boot/grub/menu.lst

You'll see a sample section for Windows, which you'll want to uncomment and add to the boot menu list in whatever position you want it in. (uncomment by removing the #'s)

    # title   Windows 95/98/NT/2000
    # root   (hd0,0)
    # makeactive
    # chainloader   +1

---

### Post by cernoch on 2008-06-13
> **meierfra. said:**
> I think this is you problem.  Grub is getting confused. According to "find /boot/grub/stage1" your ubuntu partition is "(hd0,5)". Since grub starts counting at zero, that translates into "/dev/sda6". But according to "fdisk" your ubuntu partition is "/dev/sda5".

Testdisk (see my signature) might be able to fix your partition table.

BIG THANKS TO YOU! that was just what I was looking for.

I suspected some bogus partition record, but none of the utils I tried helped to identify the problem, let alone fix it. this was perfect

heatblazer:
Czech Republic here. thanks for trying to help

---

