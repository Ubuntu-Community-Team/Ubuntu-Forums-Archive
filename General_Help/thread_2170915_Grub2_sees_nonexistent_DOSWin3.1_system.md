---
title: "Grub2 sees nonexistent DOS/Win3.1 system"
date: 2013-08-28
forum: General Help
---

### Post by Iron_Mew on 2013-08-28
I have my hard disks configured as follows:

sda1: NTFS - system partition for Win7 x64
sda2: NTFS - user data partition
sdb1: ext4 - system partition for Bodhi Linux
sdb2: NTFS - more user data

When I run update-grub I get this:

```
[ironmew@longcat:~]
> sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-12-generic
Found initrd image: /boot/initrd.img-3.8.0-12-generic
Found Windows 7 (loader) on /dev/sda1
Found MS-DOS 5.x/6.x/Win3.1 on /dev/sda2
done
```

There is, of course, no MS-DOS or Win3.1 system on /dev/sda2. The additional useless line in grub2 is hardly a show-stopping problem, but I'd still rather remove it. How do I do that? I've had a look in /etc/grub.d/##_whatever but I can't see the relevant lines.

---

### Post by grahammechanical on 2013-08-28
The command update-grub is just a shell script that executes a Grub utility called grub-mkconfig which in turn creates the grub.cfg in /boot/grub/ This configuration file is composed from runing the scripts in /etc/grub.d/ and a search of the hard disk for operating systems by grub os-prober. We are not supposed to edit grub.cfg but it can be done but it will only be re-written again the next time update-grub is run.

We have to remove the circumstance that is causing the line to be detected by grub-mkconfig. So, you either have that operating system in sda2 or something on sda2 that is being taken for an OS or there are references to it in one of the files in /etc/grub.d/ To make changes to grub.cfg we edit a file in /etc/grub.d/ and then run update-grub.

Have you at some point created a custom configuration file? There are two in grub.d/  40_custom and 41_custom. They are basically blank and are there to be used as templates for creating our own custom files with a similar naming style such as 15_custom.

Examine /boot/grub/grub.cfg and look for the line that begins

> ### BEGIN /etc/grub.d/10_linux ###

And the look for any line that begins

> menuentry

and

> submenu

If you are using Ubuntu 12.10 or 13.04

These are the entries that appear in the grub menu. Under each menu entry look for the line that says something like

>     set root='hd1,msdos8'

That is taken from my grub.cfg. hd1 = the second hard disk = sda2. hd0 = first hard disk = sda. msdos8 = 8th partition on second hard disk. So, you are looking for a menu entry that has a set root='hd0,msdos2'  More than this I cannot help you with.

Regards.

---

### Post by tgalati4 on 2013-08-28
Perhaps you had FAT32 on /dev/sda2 at some point?  Maybe the partition table didn't get written completely, or correctly?  Can you see the data in /dev/sda2 from both Windows and Linux?  If so, then it shouldn't be a problem, since you can't boot into it.  Just comment out the entry and you should be OK.

---

### Post by oldfred on 2013-08-28
Do you have command.com in sda2 at top level?

I did not know os-prober still found the old systems but it must. It primarily looks for boot files.

---

### Post by omelette on 2013-08-28
I had this problem and someone here pointed me in the right direction.  It was caused by hidden boot-files from a deleted WinXP install on a NTFS partition.  Just delete them and update Grub2, problem solved - at least it was for me!  Thread found [here]("http://ubuntuforums.org/showthread.php?t=2040220").

---

