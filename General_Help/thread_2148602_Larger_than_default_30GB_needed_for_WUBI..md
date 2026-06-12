---
title: "Larger than default 30GB needed for WUBI."
date: 2013-05-25
forum: General Help
---

### Post by usalabs on 2013-05-25
I saw in a closed post someone requested the default limit of 30GB for WUBI to be extended, but was more or less informed that the default limit is NOT going to be lifted simply because if more space is needed, then to install a full Ubuntu on a dedicated partition, well, he/she is WRONG!, the idea of WUBI is to have Ubuntu installed inside windows so that if for some reason something goes wrong with Ubuntu, then all one has to do is to boot into windows, and use the control panel add/remove to uninstall Ubuntu, Ubuntu is then uninstalled, and the mbr restored, using a dedicated partition, Ubuntu would write it's own mbr and us it's own boot loader, so if anything goes wrong with Ubuntu, or one no longer wants Ubuntu installed, then using a dedicated partition, one would need to have the original Windows CD to restore the MBR and go through all sorts of procedures to remove the partition, sooo, to have a selectable size of WUBI larger than 30GB would be beneficial to both windows and Linux users.

There's nothing to say one has to keep Ubuntu installed,,, what if one wants to try Xubuntu, or Lubuntu, or even Mythbuntu, I for one would like to be able to use WUBI larger than 30GB.

---

### Post by ibjsb4 on 2013-05-25
WUBI is being dropped all together.  

[https://bugs.launchpad.net/ubuntu-manual/+bug/1166653](https://bugs.launchpad.net/ubuntu-manual/+bug/1166653)

---

### Post by usalabs on 2013-05-26
> **ibjsb4 said:**
> WUBI is being dropped all together.  

[https://bugs.launchpad.net/ubuntu-manual/+bug/1166653](https://bugs.launchpad.net/ubuntu-manual/+bug/1166653)

Well The devs have done it again, 1st they force a new desktop on people that find it completely useless, (Unity), and now WUBI is being dropped? I guess I won't be using Ubuntu anymore

Personally I find WUBI a great idea when installing Ubuntu as a windows installer, and not having to "Force" people to either wipe out their entire HD to install Ubuntu, or the headaches in partitioning the HD then when something goes wrong, completely screwing up Windows and having to utilize the Recovery partition just because of an Ubuntu screw up, thus loosing everything that was in windows, whereas using WUBI, is ideal to install Ubuntu inside windows without the hassle of partitioning, and should anything go wrong with Ubuntu, one only has to go to windows control panel add/remove and remove Ubuntu with no disruption to windows.

My experience in using windows and Linux, I find one can't use just Linux or windows, because Linux is great for music production, audio and midi, but crap for video editing, whereas windows is excellent for video editing when using Cyberlink's PowerDirector, which has features that are not available in ANY Linux video editing software (I know I've tried every video editing app out there for Linux), also, 64 bit Linux is (imo) 1000 time slower than 32 bit Linux, and 64 bit linux does not have backward compatibility for 32 bit apps, whereas 64 bit windows does.

So, personally, I prefer to use both Linux and Windows, but if WUBI is being dropped, then I'll just have to put up the MS's annoying bits of windows (such as the UAC), and only use Linux (OpenSuSe) for my web server.

---

### Post by mcduck on 2013-05-26
There are numerous, very easy to sue, bootable CD's that can restore the Windows bootloader for you. And Windows itself is also able to create one for you. So you really don't need to reinstall your Windows from recovery partition just to get the Windows bootloader back.

Furthermore, Wubi installs aren't, and never were, intended for anything more than testing Ubuntu before making a proper install. Their performance is not on the same level with a true install, and theya re much more likely to break. (Especially any errors on the Windows filesystem would break the Wubi install as well).

Also 64-bit Linux is easily capable of running 32-bit applications, you just need to install the required library to enable that. Although in most cases that shouldn't even be needed as most of the applciations are already available as 64-bit versions since it's more or less a trivial thing to do on open-source platform.

Then, to test Xubuntu, Lubuntu or other Ubuntu variants, you don't need to make a fresh install. Apart from the default included packages they are all one and the same OS, so you get the same result simply by adding the desktop metapackage for which ever version you want t o try. And you can run all of them from the same install, selecting which desktop t use at the login screen.

(and finally, these are *user* forums and it's quite rare to see any developers around here, so while venting out your opinions here might make you feel better, it's not a place to make complaints if you want them to be seen by anybody who's actually able to do anyhting about them...)

edit: Anyway, the devs aren't "forcing" any desktop on people either. The last time I checked there were quite many different desktop environments and window managers available in the official repositories, ready for anybody to use install and use should they want to. Plus of course all the ubuntu variants that come with different desktop straight from the install...

---

### Post by kurt18947 on 2013-05-26
Two words -- Virtual Machine.  When I had one, I had Ubuntu as the host, Windows as the guest.  There are boot managers for "MSDOS" formatted disks and my sketchy understanding is that UEFI alleviates the problem with boot managers.

---

### Post by ibjsb4 on 2013-05-26
+1 to kurt18947

Been using VirtualBox for a few years and once you get pass the learning curve it can make life a lot easier.  You no longer have to worry about screwing up your windows boot.  You now have full backup and restore (called a snapshot) that can be done in a few clicks of the mouse.  No longer need to burn a CD/DVD to try out a distro (it can be loaded to a VM straight from the host).

The big drawback being you got to have enough resources (cpu, ram, disk space).

---

### Post by usalabs on 2013-05-26
After hours of google search I finally found the answer to my question, if anyone wants to keep using WUBI and want to increase the size of their existing WUBI installation, check out this site:- [http://linuxnick.blogspot.com/2012/06/how-to-increase-size-of-your-existing.html](http://linuxnick.blogspot.com/2012/06/how-to-increase-size-of-your-existing.html)

---

### Post by ibjsb4 on 2013-05-26
Congratulations :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by kurt18947 on 2013-05-27
It's also not unheard of to see a thread similar to this:

Poster #1:  I'm having this problem............

Poster #2:  Strange, I've never seen that

Poster #3:  Nope, me either

Poster #1:  But my Windows is fine .........

Poster #2:  Uh, is the a WUBI install?

Poster #1:   Yeah but .....

Poster #2 &3:  Ahhhhh

Problems do crop with with WUBI installs that do not show up in regular installs.  I think that's the primary reason WUBI is being discontinued.  I've not used a WUBI install; my understanding is that it's fine for becoming familiar with Ubuntu but asking it to perform more than very elementary tasks (which can be performed nicely in a 30 GB. partition) is asking more than what is intended for a WUBI install and problems crop up that don't show up with regular or VM installs.

---

### Post by Mark Phelps on 2013-05-27
Congrats on figuring out how to resize Wubi ... but ... a couple of points to consider:

1) There is no need to restore the MBR when getting rid of Wubi because it does NOT modify the MBR in the first place!  Wubi modifies the Windows BCD to add an entry for Ubuntu, not the MBR.  If the entry is not removed when you uninstall Ubuntu, there are Windows GUI-based tools that can do that easily.

2) Wubi has been discontinued -- starting with 13.04.  So, you're comitting yourself to a product that is already being killed off.

---

