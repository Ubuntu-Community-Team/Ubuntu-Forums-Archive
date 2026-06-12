---
title: "Sound problems"
date: 2007-01-01
forum: General Help
---

### Post by Keldek on 2007-01-01
I'm having trouble getting multiple applications to use sound at the same time, ie. when I'm playing a game, I get no sound when playing music... or if I start my music first, I get no sound in the game.

I've done searching online and all I could find was to make the following changes:

In "/etc/esound/esd.conf"

```
[esd] 
auto_spawn=0
spawn_wait_ms=100
default_options= -terminate -nobeeps -as 2
```

In "/etc/libao.conf"

```
default_driver=esd
```

but to no avail.

---

### Post by Keldek on 2007-01-01
anyone have any info on how to go about fixing this issue?

---

### Post by Keldek on 2007-01-01
additionally, my current sound driver is as follows: 'Ali M5455', but as per my mobo (Asrock 939dual-sata2) specs I use the following codec: 'Realtek 850 7.1channel AC'97 audio'; which leads me to believe that I have the wrong audio drivers installed. Maybe this is the cause of my problem? Being a linux newb still, and withno luck searching the various howto's, any help getting the proper sound driver installed would be greatly appreciated.

---

### Post by pseudonym on 2007-01-01
some games don't work well with the esd sound server. From memory (I don't use gnome anymore), typing 'killall -9 esd' before starting the game usually helps. This stops the esd process running in the background. You should also be able to turn off esd on logging in - look in your system properties menus for a dialogue box relating to it. 

Also, if you haven't already, check out the [Comprehensive Sound Guide]("http://www.ubuntuforums.org/showthread.php?t=205449") on these forums.

---

### Post by Keldek on 2007-01-01
hmm. I followed the instructions for reinstalling a fresh kernel driver, as explained in the guide you posted, rebooted the system and now get this:

> User's $HOM/.dmrc file is being ignored. This prevents the default sessions language from being saved. Files should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

I haven't changed anything except for the changes I made in my original post and reinstalling the fresh alsa drivers. And I'm now even more baffled than I was before hehe.

---

### Post by pseudonym on 2007-01-01
I don't know what's gone on there but it looks like you can rescue the situation. Have a look at [this]("http://www.linuxquestions.org/questions/showthread.php?t=478089") . Google often works wonders with error messages like that. ;)

---

### Post by Keldek on 2007-01-01
aye hehe, I was actually just reading that same exact thread :D

I'm sure I can resolve this issue but the sound issue is still unsolved :cry:

I'm actually gonna try my luck at installing KDE and see how that goes (KDE has always been my favorite for some reason). Much thanks for the help so far :)

---

### Post by pseudonym on 2007-01-01
If it's not gonna be too much of a pain I'd also consider a re-installation of Ubuntu. Unresolved sound issues have a nasty habit of comming back.

A tip for future installs: Have a partition scheme like this - ```
Root|Swap|Home|Others if you use them
``` 10GB is a good size for your root partition. Set up like this you can easily back it up using the partimage imaging utility, which can be found on the [System Rescue CD]("http://www.sysresccd.org/Main_Page") . 

Then if you're system gets broken somehow, you can just overwrite it with your saved image file, and you'll be back to where you were before it broke. Back up once a week like this, and you will have good peace of mind. :)

---

### Post by Keldek on 2007-01-01
hmm, that sounds interesting actually, kinda sorta how I set up my 'doze partitions (well, I use 1 partition for main system files, 1 partition for 3rd party programs, 1 partition for music, etc...).

As I haven't actually installed much, reinstalling ubuntu won't be that big of a hassle for me, but I do have a few questions before I attempt this.

1. By using several partitions, how would I get Ubuntu to recognize what I'm doing? 

2. The root partition would maintain all of my direct system files, all apt-get installs, etc from the sounds of it yes?

3. I'm assuming that initially, the user /home directory would be set to the main "root" partition and I'd have to later change the 'home' directory to the partition I set up manually after install/update/login?

I have 30GB of space available atm for my Ubuntu install. For the moment, this 30GB is on my IDE drive which also has approx 180GB NTFS partition on it as well.

So if I understand you correctly, I could partition like so:

'root': size: 10GB - type: ext3
swap: size 1GB - type: linux-swap
'Home': size 19GB - type: ? (another ext3 partition?)

---

### Post by pseudonym on 2007-01-01
> **Keldek said:**
> 1. By using several partitions, how would I get Ubuntu to recognize what I'm doing?
what do you mean recognize? You can set up as many partitions as your drive can handle and as is practical for you. They will all be specified in /etc/fstab. Linux is smart enough to know about them all ;) 

> **Keldek said:**
> 2. The root partition would maintain all of my direct system files, all apt-get installs, etc from the sounds of it yes?
Yes.

> **Keldek said:**
> 3. I'm assuming that initially, the user /home directory would be set to the main "root" partition and I'd have to later change the 'home' directory to the partition I set up manually after install/update/login?
No. All partitions can be set up when you install Ubuntu. you have no reason to do any of that afterwards. Your /home directory will always be on your /home partition (even thoough in a file browser it might seem like it's on / ).

During installation you will have the opportunity to set a separate mount point for /home and any other partition you create. Just make sure to choose 'manual partitioning' when asked.

> **Keldek said:**
> I have 30GB of space available atm for my Ubuntu install. For the moment, this 30GB is on my IDE drive which also has approx 180GB NTFS partition on it as well.

So if I understand you correctly, I could partition like so:

'root': size: 10GB - type: ext3
swap: size 1GB - type: linux-swap
'Home': size 19GB - type: ? (another ext3 partition?)
Yes, but you don't need any more than 512MB swap, unless you're thinking of using stuff like 'suspend to disk' and hibernation (and even then 512MB is probably enough).

Also, if you're not going to be installing much stuff, and/or you don't have a DVD burner, and you make sure to install any games into /home (you should do that anyway), then you could probably drop your 10GB root partition back a gig or two to pick up a little extra space.

good luck!

---

### Post by Keldek on 2007-01-01
>  Originally Posted by Keldek 
1. By using several partitions, how would I get Ubuntu to recognize what I'm doing?

what do you mean recognize? You can set up as many partitions as your drive can handle and as is practical for you. They will all be specified in /etc/fstab. Linux is smart enough to know about them all

I worded that completely wrong :p, but you answered it in question 3 :)

I have a dvd burner and do plan on installing more programs over time. I'm actually eventually going to completely rid of windows completely, so I'm using the 30GB as a starting point to familiarize myself more with linux. I have a lot of non-open source proggies I use in 'doze for work (photoshop, premiere pro, etc) in which I have to find suitable programs to replace those, or an emulator that supports them (ie. crossover office or wine, etc)

I wanna rid of 'doze completely but not until I learn how to use linux comfortably.

Thanks a ton for the info, I really appreciate it :)

---

### Post by pseudonym on 2007-01-01
> **Keldek said:**
> Thanks a ton for the info, I really appreciate it :)
You're most welcome. I accept Paypal and all major credit cards :D

Anyway, I wish you success in that. There's always plenty of help here on these forums if you need it. :)

---

### Post by Keldek on 2007-01-01
An offtopic question for ya :P

I saw the "wintendo" in your sig. Is that a complete emulator like Wine/Cedega or is it just a game management system (still need wine/cedega installed to run games)?

---

### Post by pseudonym on 2007-01-01
> **Keldek said:**
> I saw the "wintendo" in your sig. Is that a complete emulator like Wine/Cedega or is it just a game management system (still need wine/cedega installed to run games)?
lol, no, what it is, is [this]("http://www.ubuntuforums.org/showpost.php?p=1929486&postcount=22") :)

---

### Post by Keldek on 2007-01-01
lol, so it's only a windows system you use explicitly for gaming, and has nothing to do with [this project ]("http://sourceforge.net/projects/wintendo/") ?

If so, I'm now sad because it sounded like a better way to play 'doze games in linux through 'doze (something or another lol)

---

### Post by pseudonym on 2007-01-01
> **Keldek said:**
> lol, so it's only a windows system you use explicitly for gaming, and has nothing to do with [this project ]("http://sourceforge.net/projects/wintendo/") ?

If so, I'm now sad because it sounded like a better way to play 'doze games in linux through 'doze (something or another lol)
Damn! Someone beat me to it! :) Oh, well, I guess it didn't take *that much* imagination to think of the name. Still, i hope he hasn't copyrighted it. :-k Although with no activity in over 2 years, I think it's safe to say that project's dead.

No, as you found out, 'Wintendo' for me is just my cheap rationalisation for continued windows use. It's cheap, but it helps me sleep at night :)

---

### Post by Keldek on 2007-01-01
I definately like the idea :D

One of these days, when I can manage to get abode premeire pro & photoshop running on linux (or learn how to thoroughly use an alternative to those proggies.. ugh!) I'll probably do the same thing lol. Probably won't be any time soon though :( since it took me forever to learn premeire pro and I don't really have the time to learn an alternative to replace it.

One day, within the next 100 years, software developers around the world will bow before linux and *at least* make a *nix compatible version. Until this day comes, Micro$oft will continue to suck money from us like the leeches they are! :(

---

