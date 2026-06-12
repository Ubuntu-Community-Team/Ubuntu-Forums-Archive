---
title: "Grub Error 16"
date: 2008-04-22
forum: General Help
---

### Post by halw on 2008-04-22
Have a multi boot system (Mepis, XP & Ubuntu) using Mepis grub. Had system open to clean and add memory. Upon powering system back up, all OS's boot with the exception of Ubuntu v7.10. When attempting to boot into Ubuntu I get a grub Error 16: inconsistent filesystem structure.

What could be the cause of this and is there a way to fix it?

Also, could someone point me to where the instructions for rebuilding grub from Ubuntu are?

---

### Post by phidia on 2008-04-22
You could try to run fsck or e2fsck on that partition while it's unmounted either from one of your other installs or a livecd. 

See grub errors [here]("http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html")

"Rebuilding" grub would normally just be a re-install and you can do that by following the how to [here]("http://ubuntuforums.org/archive/index.php/t-24113.html").

---

### Post by Herman on 2008-04-22
:) Hello, your Ubuntu partition just needs a file system check.

The best idea is to boot your Ubuntu Live CD in your computer.

What partition number is your Ubuntu partition, (in Linux terms)? 
Is it '/dev/hda2', or '/dev/hda6' or something like that? 
Find out by taking a look with Gnome Partition Editor or run the command 'sudo fdisk -lu to check,
```
sudo fdisk -lu
```Then, when you know which partition number your Ubuntu partition has, run a file system check on it from the command line in your Ubuntu Live CD.
My favorite file system checking command for checking and repairing an ext3 file system is this one,
```
sudo e2fsck -C0 -p -f -v /dev/hda2
```Where: hda2 is your Ubuntu partition.
That command is a safe one to begin with, and it will fix your file system in most cases.
If it can't, it will tell you what's wrong and maybe even what command to run next.
If you can't understand what it's trying to say, come back here and I or someone else around here will help you more.

What to do mean by 'rebuild' GRUB?
GRUB has files in /boot/grub, and in several other locations in your file system. 
It is rare, but sometimes those are missing or corrupted somehow, perhaps from a faulty installation.
They can be renewed by running the GRUB program in /usr/sbin.
Again, to do that you need to know which is your Ubuntu partition, and what your hard drive is called in Linux terms, such as '/dev/hda', or '/dev/sda'.

The following commands need to be run with Ubuntu booted, or you will need to know how to chroot into your hard disk installed Ubuntu system from your Live CD. If your system won't boot, it is simpler to boot with [Super Grub Disk]("http://sgd.benjamin-butschko.de/")  and run these with Ubuntu booted.

The command to rebuild your GRUB files in /boot/grub and at the same time re-install Ubuntu's GRUB in the MBR is something like, 'sudo grub-install /dev/hda'
```
sudo grub-install /dev/hda
```Where: '/dev/hda' is where you want to install GRUB's stage1 code, it can be to MBR in any hard disk, or to the boot sector of any Linux partition, normally your Ubuntu partition.

The command to rebuild your /boot/grub/menu.lst file or generate one if none exists in /boot/grub is 'sudo update-grub'
```
sudo update-grub
```I don't recommend rebuilding GRUB unless you really need to, as you will lose your current GRUB settings. (Unless you make a backup of your /boot/grub/menu.lst file to some other directory, such as your /home/username folder).

Normally, the commands I just gave you are not necessary.

If you just want to re-install GRUB, it is better to use the easier and gentler 'sudo grub', 'find /boot/grub/stage2', 'root (hd0,1)', setup (hd0)', 'quit' series of commands. Those are safer.
Here's a link about those in case you don't know them, [Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").

Regards, Herman :)

---

### Post by halw on 2008-04-22
```
fsck /dev/sdb1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sdb1: clean, 141745/19169280 files, 3355146/38315017 blocks
```

As you can see from the above 'fsck' came back with a clean bill of health on sdb1 (my ubuntu partition). What next, rebuild grub?

---

### Post by halw on 2008-04-22
> **Herman said:**
> :) 
```
sudo e2fsck -C0 -p -f -v /dev/hda2
```Where: hda2 is your Ubuntu partition.
That command is a safe one to begin with, and it will fix your file system in most cases.
If it can't, it will tell you what's wrong and maybe even what command to run next...


Regards, Herman :)

Thanks Herman, that did the trick.

---

### Post by Herman on 2008-04-22
Yes, fsck is a great program and it's usually the first thing people thing of when they need to have a file system checked.
What most people don't realize though, is that fsck runs e2fsck for you, but with only the options that fsck thinks you need.
When we run e2fsck ourselves, we can specify the full range of options, so sometimes when fsck doesn't do it, e2fsck might work, (providing of course we use the appropriate options).

Thanks for your feedback, I'm glad to read that helped you,
Regards, Herman :)

---

### Post by halw on 2008-04-24
Did it again. Ran the following
```
e2fsck -C0 -p -f -v /dev/sdb1
```

Back up again. Not sure what is causing error. Guess I will have to check sata connection to drive. Maybe something came loose while cleaning the other day.

---

### Post by halw on 2008-04-25
Update: Swapped out the SATA cable on the drive with Ubuntu on it. System has rebooted successfully something like 3 times now.

FWIW, I've heard that SATA cables are touchy little things. So maybe when cleaning the inside of my pc the other day something got jostled. Will update again after a few more boots.

---

### Post by Herman on 2008-04-25
:) Okay, thanks for that information, keep me posted. That might help someone else some day, I didn't realize that SATA cables might be the cause of booting problems but it seems to make sense, they well could be.
I'm adding that possibility to my collection of possible causes for [Grub error 16]("http://users.bigpond.net.au/hermanzone/p15.htm#16"), thank you halw. :)

Regards, Herman

---

### Post by halw on 2008-04-26
Have booted the system several times now with no issues. I feel comfortable, at this point, that the SATA cable with the cause of the boot issues.

Thanks to all who responded to my query.

---

