---
title: "What are the disadvantages of Wubi?"
date: 2007-06-22
forum: General Help
---

### Post by fedira on 2007-06-22
I'm basically a Linux newbie, although I've played with baby distros like PuppyLinux, used a few live cds (including Ubuntu), and regularly use a FreeBSD-based flavor of UNIX at work. I think I'm finally ready to install Ubuntu on my Windows laptop at home, and I have a few questions.

I understand (in very basic terms) how Wubi works, and it sounds almost too good to be true. A full installation of Ubuntu without all of that tricky (for beginners!) partitioning stuff? Amazing. So -- I want to know -- what is the catch? For people wanting to do a dual boot, what are the *disadvantages* of Wubi? If Wubi's so much easier, why wouldn't everyone setting up a dual boot with Windows use it? Is it much slower? Is it harder for Ubuntu to detect external hardware, internet, etc if it's installed using Wubi rather than with a standard partitioned setup? Is Wubi really intended for people who are just trying Ubuntu, not for those who plan to use it on a daily basis?

I know there's *some* discussion [here]("http://ubuntuforums.org/showthread.php?t=396561") about the good and the bad of Wubi, but I didn't see somewhere where this question was specifically addressed.

Help and feedback would be greatly appreciated. Thanks!

---

### Post by ago on 2007-06-22
Good question, at the moment:

1. Disk performance is slightly slower. You should not be able to notice any difference under normal circumstances. The problem becomes more evident if you have little memory and use swap a lot or if your windows partition is very fragmented. It should be still far faster than under a typical VM or LiveCD.

2. The filesystem is less reliable than in a real installation. This is because you have 2 filesystems nested within each other which makes it more vulnerable than ntfs or ext3 taken individually. This can be an issue if you hard reboot (unplugging the power). Hard reboots are never ever a good idea, but even less so in wubi. We have taken some measures to minimize the risk (and will add a couple of tricks to next build), so that hard reboots can be better tolerated, but the rule of thumb is: do not hard reboot. In linux there are alt+sysrq key combinations if you get stack for any reason. 

3. Hibernation / Suspend does not work properly. We are looking into this with the help of some ubuntu kernel devs. Either we'll fix that or we will disable hibernation/suspend.

A side issue is that with wubi people tend to allocate less disk space than they would with a normal installation (since they take it as a trial and then keep using it). Of course if the free space is over, it is going to create issues, but that is hardly our fault. We are looking into ways to expand virtual disks, but that would be a separate app anyway. That said in linux you can create a link from a folder within a real partition to a folder within a virtual disk, thus alleviating the pain.

In short: allocate enough space, do not hard reboot and do not suspend/hibernate. Other than that it should be the full monty: same speed (other than for #1), same hardware support/detection, same behaviour, same software. A small trade-off considering that we* provide what can possibly be considered the easiest OS installer ever created, whatever the OS.

As for long term use, I would consider wubi as a mid-term solution. You can use it happily for weeks and months, but because of the 3 issues above, if you find yourself using Ubuntu quite heavily, you might want to do a full installation later on. That said we have a tool to migrate virtual disks to a real partition (LVPM by tuxcantfly). So migration should be quite smooth (that should result in an installation which is 100% identical to a standard one while keeping your data and settings). 

If you have a free partition or a spare hard disk and are confident about partitioning and ISO burning there is no much reason to use Wubi, just go straight for the full installation via live CD. But for people that do not know what a partition is, wubi is probably the best solution to date, particularly once tools such as LVPM reach final status. I hope that wubi will bring a small revolution to Linux installers and hence to Linux adoption, similar to what Knoppix/LiveCD did a few years ago', and I would not be too surprised to see Wubi clones implemented by other *nix distros in the near future. 

FYI: Wubi will hopefully become an official installation method by next Ubuntu release and we will "merge" with Ubuntu. Even though the recommended long term installation will still be based on the current LiveCD installer (with partitioning), Wubi installer will also be available on the official CD and as a separate download. By Gutsy we will use the LiveCD ISO as opposed to the Alternate ISO as a source of packages and the installer will be fully "graphical".


* A big chunk of the merit goes to the people that gave us the possibility to boot linux from within windows (grub4dos) and provided us with r/w access to ntfs (ntfs-3g), without such technologies wubi would not be possible today.

---

### Post by edea on 2010-10-21
I have the same question, but considering 3 years have passed since the answer, has anything changed?
What are now (for example in an installation of Maverick) the disadvantages of Wubi?

---

### Post by doon41 on 2011-03-03
Yes, another would-be Ubuntu novice also wants to know.  Anything new beyond the above, very clear and excellent answer? -Doon41

---

### Post by steveneddy on 2011-03-03
W - Windows wants to be the only OS on the HD
U - Ubuntu doesn't mind sharing
B - Booting Linux or Ubuntu is cool
I - I hate Wubi

Actually, Wubi is only meant for a short trial period and is not recommended for long term installations. Wubi also will probably break your Windows install if windows is having issues - even issues that you don't currently know about.

My suggestion is to run Ubuntu in Virtual Box - much easier to USE Ubuntu without having to actually partition the drive.

---

