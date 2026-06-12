---
title: "Increasing ubuntu's memory usage to improve performance?"
date: 2008-05-09
forum: General Help
---

### Post by malfist on 2008-05-09
I have 1.5GB or RAM. I have yet to see Ubuntu use more than 1GB nor more than 50MB SWAP. Is there a configuration I can set to tell ubuntu to free RAM less aggressively? Or the ability to keep some programs running all the time in memory like firefox or OOo or some of the programs that take a while to launch so they could launch a lot faster?
I know what it's like running DSL from RAM only, I wish I could do that for ubuntu.

edit: I've already set vm.swappiness = 10

---

### Post by sdennie on 2008-05-09
Are you sure it's not using the full 1.5G if you include the cache?  If you bring up a terminal and type "free -m" and look in the "used" column that will tell you how much memory is actually being used.  The cache is more or less doing what you've asked for: It's keeping stuff that has been previously used, but is no longer being used, in RAM (specifically to keep from having to read it from the disk again).

Edit:
Got free backwards.

---

### Post by jabagawee on 2008-05-09
Note: the following is all IMHO. Congratulations! You just achieved RAM nirvana: you're using less than you have. When the need arises, your RAM usage will surely rise. If you really feel like stressing your computer and using more RAM, may I suggest simultaneously running AmaroK, Firefox, OOo, and a few full screen games at once?

PS. The 50M of swap should be able to be fixed, but I doubt it'll make much of a performance boost.

---

### Post by jocko on 2008-05-09
> **malfist said:**
> I have 1.5GB or RAM. I have yet to see Ubuntu use more than 1GB nor more than 50MB SWAP. Is there a configuration I can set to tell ubuntu to free RAM less aggressively? Or the ability to keep some programs running all the time in memory like firefox or OOo or some of the programs that take a while to launch so they could launch a lot faster?
I know what it's like running DSL from RAM only, I wish I could do that for ubuntu.

edit: I've already set vm.swappiness = 10

Set vm.swappiness = 0. That will decrease swapping even more, but I don't think it will significantly alter the overall memory usage.

---

### Post by malfist on 2008-05-09
```

jerome@jerome-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1519        651        867          0          1        417
-/+ buffers/cache:        232       1286
Swap:         5169          0       5169

```

Are you familiar with what DSL's toram option does? It mounts the ramdisk and uses it instead of the harddrive (LiveCD option only). Thus loading all the programs and everything into RAM. When a program needs to launch, instead of loading parts of it from one of the slowest (if not the slowest) part of the computer, the hard drive, it loads it from RAM. DSL is only 50MB, Ubuntu is huge. Is there a way to so that, or something similar (with only some programs) in ubuntu?

I run preload, I've profiled my bootup, etc. But I want to milk more out of my system. Can I run WoW readily under XFCE or does WINE needs parts of GTK or KDE?

Anyways, my motherboard has pissed me off for the last time and machspeed's All America (made in Taiwan), life-time warranty including overclocking (disabled) shuts off USB on boot up and only way I can get it back is through pulling the plug (simple reboot doesn't do that) and half the time I lose RAM/CD-ROM/Sound Card from one boot to the next. But guess what? Machspeed's QA checked it out and it's my flaky RAM, my flaky CD-ROM, my BIOS config for the USB issue (strangely enough, I really haven't touched the CMOS/BIOS since I got it and it hasn't always had this issue) and they won't replace it.

I figure if I'm going to replace it, why stick with Socket A and an AMD Athlon XP 3000+? I've got a full-time summer job as a programmer, I can afford (while living with parent's ofcourse!) to purchase a nice shine new motherboard and the pretty little AMD Black Quard Core I've been eyeballing at newegg.

/rant

---

### Post by sdennie on 2008-05-09
You can do things similar to DSL using tmpfs but, with all the interdependencies of Ubuntu, I'm not sure you can do it efficiently so you may not see that large of a speedup for a particular app.  The other thing you can try would be using [readahead]("http://ubuntuforums.org/showthread.php?t=565651") .  Lastly, why not just never shutdown applications if you are worried application startup time and are willing to sacrifice memory to improve it?

---

### Post by NightwishFan on 2008-05-09
Prelink and Preload are designed to speed up application load times. They are in the repos.

---

### Post by malfist on 2008-05-09
I just installed prelink, I hadn't heard of it before. Preload is already running.

---

### Post by NightwishFan on 2008-05-09
Linux handles memory in an already agressive way, prelink and preload should help if you have loads to spare.

---

