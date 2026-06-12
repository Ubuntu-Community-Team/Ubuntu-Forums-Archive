---
title: "No luck booting live CD"
date: 2005-08-15
forum: General Help
---

### Post by Symo on 2005-08-15
Hello out there,

I've written twice before with the same problem but got no reply. I'll try to give more details this time and maybe I'll get third time lucky. I'm totally new to Linux and find it a bit disheartening to not even be able to load up the live CD but it'd be a shame to give up on Ubuntu already - I like all that "Linux for Human Beings" stuff. Still if the problems encountered now are a sign of things to come then I don't know if my computing and problem solving capabilities (and willpower) match up to the challenge.

Anyway, instead of blabbering, here's the problem:
When I try to boot from the live CD I come to a blue screen with a grey band on the bottom. On this grey band is written "BusyBox v1.00 - pre10 (Debian 20040623 - 1ubuntu13) Built-in shell (ash) Enter 'help' for a list of built-in commands ~#"
Is this familiar to anyone? And what are you meant to type in? I noticed that if you load up in expert mode you also come to the same point.

Some of my computer details:
Intel Celeron processor 434 MHz
128 MB RAM
Computer: ACPI PC
Harddisk: Fujitsu MPE 3084AE
CD-ROM unit: SAMSUNG CD-ROM SC-140F

Hope this suffices.

Thanking you in advance for your advice.

Symo

---

### Post by fragmental on 2005-08-18
[QUOTE=Symo]Hello out there,

I've written twice before with the same problem but got no reply. I'll try to give more details this time and maybe I'll get third time lucky. I'm totally new to Linux and find it a bit disheartening to not even be able to load up the live CD but it'd be a shame to give up on Ubuntu already - I like all that "Linux for Human Beings" stuff. Still if the problems encountered now are a sign of things to come then I don't know if my computing and problem solving capabilities (and willpower) match up to the challenge.

Anyway, instead of blabbering, here's the problem:
When I try to boot from the live CD I come to a blue screen with a grey band on the bottom. On this grey band is written "BusyBox v1.00 - pre10 (Debian 20040623 - 1ubuntu13) Built-in shell (ash) Enter 'help' for a list of built-in commands ~#"
Is this familiar to anyone? And what are you meant to type in? I noticed that if you load up in expert mode you also come to the same point.

Some of my computer details:
Intel Celeron processor 434 MHz
128 MB RAM
Computer: ACPI PC
Harddisk: Fujitsu MPE 3084AE
CD-ROM unit: SAMSUNG CD-ROM SC-140F

Hope this suffices.

Thanking you in advance for your advice.

Symo[/QUOTE]
 Doesn't sound familiar.  Maybe you need a new live cd.  If you burned the cd yourself you can check the md5 checksum to make sure it's correct before you burn it, and there is probably a way to make sure the iso matches the cd.  If you got it from shipit...well, I guess you can order another one?  It might still be possible to run an md5 check on the cd, though I'm not sure how.  I use a program called dpasha to check md5 on windows.

Is it it an ubuntu hoary cd?

From your computer specs, it looks like your computer might struggle a little with the livecd.  It might run the full install ok, though it might have some noticeable lag(possibly not. I dunno).  128mb of memory isn't much to run a modern operating system and it's even less to run a modern operating system from a live cd since everything on the live cd runs in memory.  256mb is typically the minimum if you want the system to run reasonably well.  however, if you have ubuntu( or any other linux installed) you can use xfce instead of gnome or kde and that should improve performance somewhat.  If you dont' mind the command line you can even use a minimal window manager like fluxbox.  If you want to check out xfce you can get the xfld live cd.  Any live cd is probably going to run poorly with 128mb of memory though.

---

### Post by fragmental on 2005-08-18
[http://www.sophos.com/support/genuine-cd/md5-advice.html](http://www.sophos.com/support/genuine-cd/md5-advice.html) 

That explains a method for checking the md5 of a cd on both windows and linux however it doesn't work with win9x or ME(I'm guessing that's what you have if you don't have linux).

---

### Post by Symo on 2005-08-25
The CD I got was from shipit - I got ten of them and they all had the same effect. On another computer (not my own) they worlked fine though, so it's probably as you say and just that I have a weeny computer.

Thanks for your advice.

---

### Post by wawa on 2005-09-23
I know some computers have issues booting from live cds...mine for one. I tried knoppix, warty and even hoary before, didnt work. But had no problem doing full installation.

---

### Post by wawa on 2005-09-24
Try booting with "nolapic acpi=off vga=771"

---

### Post by eneanito on 2005-10-06
I don't believe that about 128 Ram being too litle memory for a modern OS in a live CD.  Thats could be true dsfor Ubuntu whith Open Office. 
There are any Live CDs like Puppy that runs smoothly from memory in 128 or may be 64 RAM. 

I like Ubuntu. I want run Live CD in AMD 64 but I can't yet.

---

### Post by eneanito on 2005-10-14
[QUOTE=Symo]The CD I got was from shipit - I got ten of them and they all had the same effect. On another computer (not my own) they worlked fine though, so it's probably as you say and just that I have a weeny computer.

Thanks for your advice.[/QUOTE]

I´m not sure your PC be too litle. I had been unable to run Ubuntu live CD in the most giantic machine I had figure out: an AMD64 3.0 GHz. mem 512.
X86 nor Amd64 versions of 5.04

I have ran it (X86) sucessfully in too litle machines than yours is.

Try "Puppy Chubby" (with Open Office), while get solve your prob. I Am doing so.

---

