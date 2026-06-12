---
title: "thinking of using wubi - questions"
date: 2007-06-13
forum: General Help
---

### Post by simo1234 on 2007-06-13
am i right that you dont have to partion the drive at all 

I have one 80gb hard drive with an xp install

if I install wubi -

will I be able to simply select at boot from xp or ubuntu?

then once in say ubuntu will it work as if i installed it normally

will i be able to use the same HDD in both windows and ubuntu  or do I have to partian the two seperately

thanks for any help

---

### Post by ago on 2007-06-13
> **simo1234 said:**
> will I be able to simply select at boot from xp or ubuntu?
Yes

> then once in say ubuntu will it work as if i installed it normally
Yes, but avoid hard reboots

> will i be able to use the same HDD in both windows and ubuntu  or do I have to partian the two seperately
yep no nee to repartition

---

### Post by simo1234 on 2007-06-13
> **ago said:**
> Yes


Yes, but avoid hard reboots


yep no nee to repartition


what are hard reboots


also whats the deal with this

------How do I get rid of the virtual disks and switch to real partitions, and/or get rid of Windows entirely?

This feature will eventually be incorporated into Wubi in later releases, but until then, an experimental guide is available at  [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)


so would i have access to the real hard drive (documents/ music photos etc etc from my c drive
or am i just using these virtual disk things - and that would fill up quickly


thanks

---

### Post by ago on 2007-06-13
> **simo1234 said:**
> what are hard reboots
When you unplug you computer instead of shuttidng down from the menu

> also whats the deal with this
It's a planned feature to be able to move an instualltion to a virtual disk to a real partition later on. 

> so would i have access to the real hard drive (documents/ music photos etc etc from my c drive
or am i just using these virtual disk things -
Yep you can access the virtual drive, even if linux files are self contained in a windows folder

>  and that would fill up quickly
That depends on how much you allocate and how much software you will install. An 8GB system drive should do well in normal circumstances.

---

### Post by simo1234 on 2007-06-13
but how about new documents (music etc) can you save that to the normal hdd or only up to 8gb

and you can access everything existing on the hdd from windows

---

### Post by ago on 2007-06-13
> **simo1234 said:**
> but how about new documents (music etc) can you save that to the normal hdd or only up to 8gb

and you can access everything existing on the hdd from windows

You can save files on the windows folders from withing Linux, those files will be accessible from both linux and windows. You cannot access linux files from windows easily (the ones in the 8GB file) but you can access all windows files from windows.

---

### Post by simo1234 on 2007-06-13
> **ago said:**
> You can save files on the windows folders from withing Linux, those files will be accessible from both linux and windows. You cannot access linux files from windows easily (the ones in the 8GB file) but you can access all windows files from windows.

so i will be able to access all my docs in windows (mp3's photos etc) from in ubuntu

ok but what exactly are the files in the virtual 8gb section (is this just ubuntu software only)

---

### Post by ago on 2007-06-13
try ;)

---

### Post by CrazyGuy123 on 2007-06-14
Yep, you can do what you're wanting to do.  When you've installed it, there's an icon on the desktop called "Local Disk" (or similar), which allows you to access anything on your hard drive, and save anything onto your hard drive.

---

### Post by simo1234 on 2007-06-15
is ubuntu through wubi (still not sure what wubi actually does) slower as I read somewhere how does it actually work and cun you uninstall it in windows and it clean uninstalls ubuntu


thnaks

---

### Post by Sushubh on 2007-06-15
dude wubi works and it is pretty awesome. 

i always wanted to switch to linux and wubi helped me. 

i spent on a wubi installed ubuntu for 3 weeks and now i have a regular installation :)

wubi installed linux is safe and let you run it like it is properly installed. i did not notice much slowdown on disk access... 

removing is easy... it deletes the file and edit back the boot.ini file :) latter part can be done manually if it is not performed correctly. technically i think deleting the wubi folder would remove ubuntu completely and cleaning the boot.in would remove all traces. :D

i faced problems with hard reboots... (too many power cuts and fluctuations in my area.) but otherwise its stable and pretty usable

---

