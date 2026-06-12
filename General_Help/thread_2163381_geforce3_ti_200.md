---
title: "geforce3 ti 200"
date: 2013-07-18
forum: General Help
---

### Post by k1l14 on 2013-07-18
i know this card is really, really old, but it's all i have atm.

i have read a few threads (old threads) about this and i downloaded the drivers mentioned in one of the posts, but i got some error about the kernel and the extraction failed...


old thread:
[http://ubuntuforums.org/showthread.php?t=912485](http://ubuntuforums.org/showthread.php?t=912485)

i know on windows 7, i could get 1280x768 and a couple that were higher, but on ubuntu i get 800x600 and thats it. is there something i can do? i really like ubuntu and i don't wanna go back to slug windblowz...

in additional drivers, i have nvidia_current activated, but it'd not in use.... there are two more nvidia packages in the list but when i click activate i get an error: system error: E:unable to correct problems, you have held broken packages.

the package that is mentioned in that old thread, i couldn't get installed. i purged the nvidia stuff and reinstalled it all, found that suggestion in a thread on here, somewhere... O_O

forgot to mention im on ubuntu 12.04

---

### Post by GerryB on 2013-07-18
I would contact Nvidia and explain my problem. They might suggest a particular driver that works with this card. Once again, good luck.

---

### Post by GerryB on 2013-07-19
Try booting into Ubuntu Classic or Ubuntu 2D to see if that makes a difference. Those are options when you click on the Ubuntu logo before signing in. You might automatically be on a modern card setting. I've installed Ubuntu on many many computers, including a very old A30p IBM Thinkpad built in 1997 and Ubuntu has recognized all video cards without a problem. I'm surprised that you're having one with this card. It might help to post under "Instalations and Upgrades" to get comments from more experienced users. Good luck!

---

### Post by k1l14 on 2013-07-19
im on xubuntu now, i thought maby, just maby it would work... lol

when i try to install NVIDIA-Linux-x86-96.43.07-pkg1 i get this...

 No precompiled kernel interface was found to match your kernel; would you    
  like the installer to attempt to download a kernel interface for your kernel 
  from the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?)

i hit yes a few times and then i get something about the instlation failing...

i have a feeling what i will get if i go to nvidia asking about a card thats older then dirt...lol

---

### Post by GerryB on 2013-07-20
You'd be surprised how techies think. I was sent obsolete material free once. Take a chance....

---

### Post by oldfred on 2013-07-20
This says you need the 96.43.xx driver for Linux. The newer drivers probably just do not work.
 Legacy drivers.
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

### Post by k1l14 on 2013-07-20
@gerryb: i went ahead and asked the folks at nvidia, still awaiting a response. i hope i can get this resolved, because this is my only complaint.

@oldfred: thats the package i tried, i guess i need a kernel? i have no clue how to find one let alone compile one... O_O

i messed around with xrandr and i actually got 1280x768 added, but when i set it to output i got a blank screen and had to reboot... ;0(

gonna keep my fingers crossed that i don't have to use that dreaded win7 disc again....

---

