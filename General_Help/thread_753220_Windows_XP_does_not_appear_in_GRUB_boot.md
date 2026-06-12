---
title: "Windows XP does not appear in GRUB boot"
date: 2008-04-12
forum: General Help
---

### Post by wkdude18 on 2008-04-12
I have a laptop which was installed with Windows XP. I installed Ubuntu 7.10 onto the machine, not paying attention to dsthow I installed the GRUB bootloader. Now I want to boot from Windows XP instead of Ubuntu, but it does not appear in the boot menu options. The only options are Ubuntu 7.10 something or other, Ubuntu 7.10 (refresh/recovery), and +memtest 7.10. Windows XP does not show up int the options. I find this surprising because I could've sworn that I did not remove Windows XP during Ubuntu installation. What should I do? I was trying to edit the boot commands temporarily, but I do not know how to change them to boot to XP. However, I do not even know if I have a Windows Partition, because I have no partition manager. GNOME partition manager won't install because it says it doesn't support my computer type(i386 or something). And when I check the filesystem with Nautilus File System manager it seems to ignore any Windows partition if there is any. So, therefore I also do not know how to check my partitions or change a GRUB boot command temporarily to boot into Windows:(. Should I use the Ubuntu boot CD to see my partitions? I'm really confused and have no idea what I should do...:confused:

---

### Post by jameswillmer on 2008-04-12
go to 

APPLICATIONS - ACCESSOREIS - TERMINAL

and post the results of 

> df -h

---

### Post by jameswillmer on 2008-04-12
also in terminal type

> 
cat /etc/fstab

and post results here

---

### Post by wkdude18 on 2008-04-12
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=23cd3007-03c4-4726-a2a2-9221d2d10f7f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ed09cd29-f61c-41bc-990a-abdf0dbdd5d2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  2.2G   32G   7% /
varrun                506M   96K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   64K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile


What does this stuff mean?:confused:
XP is easier to understand than this:lolflag:

---

### Post by jameswillmer on 2008-04-12
the bad news is ....as far as i can see ...  and maybe someone will confirm...

1) you have wiped windows from your harddrive - when you said you didn't pay much attention to the install process you weren't kidding.    I hope you had the data backed up

2) There is a GUI way of seeing all this data but it would have taken longer to describe it to you - that's the option you have with LINUX.    It would also have taken more effort to display here (lots of screenshots)

3) fstab stands roughly for "file system table" and contains all the resources that are "mounted" to your computer at boot.   In your case there are just two disk based partitions (sda1 where "/" or root file system is mounted and sda2 which is a swap partition)

4) command df shows you how much is used of the various filesystems.   The "-h" flag asks for display of sizes in "human readable units" ie GB insteady of bytes

Hope you had the XP data backed up!

JW

---

### Post by jameswillmer on 2008-04-12
EDIT NO HOLD ON

WHY ARE /dev/sda2 /dev/sda3 /dev/sda4 not showing up above
maybe all is not lost

can you do the following

sudo apt-get install gparted to install the full version partition manager

SYSTEM - ADMIN - PARTITION EDITOR

then take a screenshot (SYSTEM ACCESSORIES SCREEENSHOT)

also how big is/was your hard disk in windows

---

### Post by bobdob20 on 2008-04-12
The windows partition would only show up in df -h if it is mounted and i dont think ntfs are mounted by default.

To view all partitions and drives use:

sudo fdisk -l

And /dev/sda2, /dev/sda3 and /dev/sda4 would only show up if the partitions exist.

---

### Post by wkdude18 on 2008-04-13
Uh-oh. Is this a bad sign that I completely removed Windows XP? (If so I feel very stupid:()

---

### Post by Trollslayer on 2008-04-13
NTFS partitions are mounted automatically so I'm afraid the XP installation is gone.
If you haveXP installed you have to choose the option which lets you resize the Windows partition.

---

### Post by wkdude18 on 2008-04-13
Well thank you all for your help with my dumb question. I suppose that might explain why Xp does not appear in GRUB boot. Hopefully I could help one of you sometime (probably not).:)

---

