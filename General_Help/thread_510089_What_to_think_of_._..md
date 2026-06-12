---
title: "What to think of? . ."
date: 2007-07-26
forum: General Help
---

### Post by TrickyClown on 2007-07-26
What do I need to think of before installing Wubi on my computer?
I also got serious issues with Vista right now, really slow and such, and I would like
to get instead Windows XP Home Edition because It goes so much faster and such.
But the problem is that, if I change the OS, I lose my quarentee (<-Grammar) because
I can't afford the real WinXP HE, so I borrowed a CD from a friend of mine.

Also, I am going to try out Wubi, but what do I need to know before installing it?
I've seen there is a plenty of users that have got Fatal errors and HD problems.
The HD of mine is an NTFS one with right now 89gig free space.

So yeah, does also Wubi work for Vista, and is there any tutorial What-To-Do and such
because I did search around a little...


Because I would get in some trouble if I screw this up, and a little afraid to
do mistakes when it have one of those quarentee things, because else they
won't fix the computer by reinstalling Vista and just tell that I got a illegal copy
of WinXp.


Please help me out, I can't stand Windows Vista anymore. ](*,)

                    //TrickyClock @ Clockcrew.cc

---

### Post by tuxcantfly on 2007-07-26
Latest Wubi version should work fine with Vista, even if it doesn't work well with your hardware it won't do any harm (just uninstall it and you'll be back to Vista) so no need to worry too much about screwing up your system, as for a guide, the installation process is pretty straightforward, but if you need more, check out [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by TrickyClown on 2007-07-26
> **tuxcantfly said:**
> Latest Wubi version should work fine with Vista, even if it doesn't work well with your hardware it won't do any harm (just uninstall it and you'll be back to Vista) so no need to worry too much about screwing up your system, as for a guide, the installation process is pretty straightforward, but if you need more, check out [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

The most thing I am afraid of also is, if the installation fails or anything needed so I need to reinstall Wubi, and got an OS installed on the disc, how do I prevent from the Windows XP folder in the virtual HD to get into C:/ ??
As I've heard, Windows Vista gets corrupted and it will not be bootable later in the future.

Why I want to do this is to go much more forward making flashes again and play a few games properly, such as different MMORPG games and such.

---

### Post by TrickyClown on 2007-07-27
One thing more also, I did download the program, and it says that Ubuntu is going to be installed.
The thing I was requesting was a virtual HD that takes space from my only HD and in that virtual HD, I am going to install Windows XP Home Edition.
It also says it's install destination is C:/, and I just want a virtual HD created.

---

### Post by CrazyGuy123 on 2007-07-27
Asa far as I know, Windows can't be installed into the Virtual HD - it's Ubuntu that will be installed onto the "Virtual HD".  That means your current installation of windows won't be touched, and you shouldn't have any issue with the warrenty, as it won't interfere with windows.

---

### Post by TrickyClown on 2007-07-27
> **CrazyGuy123 said:**
> Asa far as I know, Windows can't be installed into the Virtual HD - it's Ubuntu that will be installed onto the "Virtual HD".  That means your current installation of windows won't be touched, and you shouldn't have any issue with the warrenty, as it won't interfere with windows.

So, I can only have yet Windows Vista, and not have dualbooting by making a virtual HD there XP is located? ..

---

### Post by CrazyGuy123 on 2007-07-28
Correct, as far as wubi is concerned.

It is possible however to have both XP and Vista, however you have to partition your disk.  If you want to do that, I suggest you look at some guides for how to do it, and THEN install wubi afterwards.   Note that partitioning isn't easy if you've never done it before, and most guides will refer to installing Vista on a machine thats already got XP rather than the other way round.  If you do it the other way round, you'll have to use the vista CD to repair the bootloader.  I suggest here isn't the best place to ask though.

If you don't want to partition your disk, but still want Vista and XP, have you considered VMware?

---

### Post by mikewhatever on 2007-07-28
The virtual disk you are talking about is created by wubi inside the C:\
> How does Wubi work?

Wubi adds an entry to the Windows boot menu which allows you to run Linux. Ubuntu is installed within a file in the windows file system (c:\wubi\disks\system.virtual.disk), this file is seen by Linux as a real hard 
You may want to read the FAQs yourself. [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

