---
title: "Will I be able to run Ubuntu 7.10 well?"
date: 2007-10-07
forum: General Help
---

### Post by gamelord12 on 2007-10-07
I run Ubuntu 7.04 in Virtual Box, with Windows Vista Ultimate as the host OS.  I assume the emulated graphics card is pretty crappy, because my window wobble effects don't work.  I know that 7.10 comes with all kinds of cool graphics effects, but I remember I tried to make my GNOME panel slightly transparent and that didn't work.  Will I be able to use these 3D effects?  If not, I believe they're enabled by default; will that cause problems?

---

### Post by rich.bradshaw on 2007-10-07
Can't use compiz/beryl or any XGL stuff in a virtual machine, as none of the emulators can emulate 3d cards at the moment.

---

### Post by rich.bradshaw on 2007-10-07
It's probably better to run Ubuntu as a real OS, then virtualise Vista - that way you get to use a proper OS whilst still having Vista to remember the bad old days :)

---

### Post by gamelord12 on 2007-10-08
If all I did on my computer was work, you'd be right.  However, I'm a gamer.  I'm using this virtual machine to test out Linux, find out what's better about it, and learn how to use it so maybe one day when open source is publicly preferred to Windows and Mac, I can completely replace Windows.  I've already rearranged my Start menu to function more like Ubuntu's application launcher.

Also, I've tried the dual-boot option, but I have a Creative X-Fi, so I get no sound.  Plus, I had a bad experience with dual-booting where, while I managed to back up all my personal files, I had to re-install Windows in a single-boot environment to get everything back.  And that is the last time I try dual-booting on a machine that has some of my sensitive data, unless they're both Windows OSes or both Linux OSes.

---

### Post by orbish on 2007-10-08
> **gamelord12 said:**
> If all I did on my computer was work, you'd be right.  However, I'm a gamer.  I'm using this virtual machine to test out Linux, find out what's better about it, and learn how to use it so maybe one day when open source is publicly preferred to Windows and Mac, I can completely replace Windows.  I've already rearranged my Start menu to function more like Ubuntu's application launcher.

Also, I've tried the dual-boot option, but I have a Creative X-Fi, so I get no sound.  Plus, I had a bad experience with dual-booting where, while I managed to back up all my personal files, I had to re-install Windows in a single-boot environment to get everything back.  And that is the last time I try dual-booting on a machine that has some of my sensitive data, unless they're both Windows OSes or both Linux OSes.

Windows can be a booger with dual boot.  In my experience, you have to use a nice partition manager to resize your windows partition to make some space for ubuntu, then install it.  You cannot install windows if your first OS is ubuntu (i'm sure it's possible, people hack this stuff every day, but it won't be very straight-forward).  As for as the sound card... it's a popular enough card that I'm sure there are solutions on the board to get you going.  Nvidia drivers will be compiled with your kernel, so watch your upgrades...  gutsy comes with write support for ntfs drives built in, so you shouldn't run into any problems there, however... microsoft isn't friendly with linux, so you'll need 3rd party drivers to write to ext2/ext3 filesystems (i've had partial success with these... sometimes they work 100%, sometimes they don't... depends on what driver you use... you can find howtos here to do it)

you can find the support on this board for just about every problem you'll encounter... i say dual-boot... you'll find yourself using windows only when you want to game (and depending on the games, you could even install them using wine... many of the newer, popular games run flawlessly)

---

### Post by strabes on 2007-10-08
Just keep your data on a separate partition. It's so easy. That way, you can access your files in windows or linux. Here's how mine is set up:

Windows
Linux
Swap
Data

---

### Post by Naatan on 2007-10-08
> **strabes said:**
> Just keep your data on a separate partition. It's so easy. That way, you can access your files in windows or linux. Here's how mine is set up:

Windows
Linux
Swap
Data

How do you get APT to install to the data partition rather than the linux partition? :)

---

### Post by gamelord12 on 2007-10-08
I'm not so sure that I'll be using Ubuntu more than Windows when I already have everything installed on Windows.  For one, I game A LOT.  Second, there are several things that Linux just can't do yet (not the OSes fault, just software).  Of particular importance, video chatting over AIM, a GUI version of Handbrake (one of my favorite and most-used programs), and installing things hassle-free that aren't covered by the package manager.

I mean, I love Vista.  It's an easy-to-use, powerful OS.  All the best software on Linux is also on Windows anyway (OpenOffice, Firefox, etc.) or there's a Windows equivalent that is also free and does the same thing.  I don't think I could make Ubuntu my primary OS until at least when the next Windows comes out (codenamed Vienna) but if that's only in 3 years, it's still not looking likely.  I would like to learn Linux though.

And as for my sound card, I had asked around these boards a few months back and it turns out that Creative is very adamant about not sharing with the open-source community that there are just no drivers for it; not even proprietary.

---

### Post by SpoZen on 2007-10-08
> **Naatan said:**
> How do you get APT to install to the data partition rather than the linux partition? :)

I was wondering the exact same thing :)

---

### Post by strabes on 2007-10-08
> **Naatan said:**
> How do you get APT to install to the data partition rather than the linux partition? :)

I don't. I use the data partition to store music, pictures, documents, etc.

---

### Post by SpoZen on 2007-10-08
> **strabes said:**
> I don't. I use the data partition to store music, pictures, documents, etc.

So there isnt anyway to install deb packages to another partition?

---

### Post by jocko on 2007-10-08
> **SpoZen said:**
> So there isnt anyway to install deb packages to another partition?

The simple answer is "no".
When you install a .deb package, different files end up in different places in your "/" file system. Some files end up in /bin, others in /lib and /etc and so on.
A slightly more complicated answer is "maybe".
You can probably set up your mount points so that some of the folders that are normally  part of your "/" partition get mounted on other partitions.
I'm not sure what good that would do, but if the different partitions were on different disks, maybe it would increase the speed of some disk read/write operations...

---

### Post by Naatan on 2007-10-08
That's what I thought, it's a damn shame to be honest.

I personally don't like how linux saves data, one program is spread across various directories, I really don't see the point.

<3 /opt

---

