---
title: "Dual-Boot [Help]"
date: 2007-09-25
forum: General Help
---

### Post by Amit9192 on 2007-09-25
Hey

How u doing all?
I installed Ubuntu and wanting to run dual boot with xp, I have no idea how to do so, i tried to put the xp disk in and restart comp, done nothing...
How do i run dual boot while Ubuntu is installed first?

Thanks for ur help,
Amit.

---

### Post by Sef on 2007-09-25
Read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing").

It seems likely that you overwrote XP.   To check, do the following:

Applications > Accessories > Terminal 

then type or copy this command:

```
sudo fdisk -l
```

Then copy and paste here.

---

### Post by Amit9192 on 2007-09-25
amit@Amit-Desktop:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
amit@Amit-Desktop:~$ sudo fdisk-1
sudo: fdisk-1: command not found

---

### Post by DouglasK on 2007-09-25
The Windows XP Install doesn't support dual booting.  As such, you'll need to install windows, then Ubuntu Linux.

Once Windows is installed, here is [WindowsDualBoot How To]("https://help.ubuntu.com/community/WindowsDualBoot") ([https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")) on the [Ubuntu Wiki Documentation Site]("https://wiki.ubuntu.com/") ([https://wiki.ubuntu.com/]("https://wiki.ubuntu.com/")). 

Print it out before you try to follow it as you'll be rebooting your computer during the process.  I've learned this the hard way more than once.    :)

I know it's not the ideal answer you want, but I believe it's the best one to get what you want in the long run.

Regards,
   Douglas

---

### Post by aashay on 2007-09-25
If i'm understanding the situation correctly heres what you should do:
Install Ubuntu (already done)
Install Windows
Boot using the Ubuntu livecd
Reinstall GRUB
Boot into Ubuntu
Configure Grub to boot into Xp

---

### Post by thelastmre on 2007-09-27
to aashay:

it appears he does not even have 2 partitions. I am in the same boat ATM. I've got Ubuntu installed on a 320gb sata formatted as ext3. I've got a gparted live CD and I want to split my HD up but I am not sure how to go about doing this. Do I need to split my 320 into 3 different partions? Something about a boot partition, then another partition to install XP on? Does XP really have to be installed first and that is the only way?

---

### Post by aashay on 2007-09-29
Xp does not have to be the first partition.. you could use gparted to make a new ntfs anywhere in your existing disk. Then install xp onto the ntfs. Next time you boot, xp bootmenu would have replaced GRUB so boot the live cd once again and setup grub. Instructions to do that can be found [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by MarkieB on 2007-10-01
> **Amit9192 said:**
> amit@Amit-Desktop:~$ sudo fdisk -1
fdisk: invalid option -- 1

that's -l as in 'L' not -1 :KS

---

