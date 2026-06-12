---
title: "[SOLVED] Stupid Boot Problem..."
date: 2008-04-03
forum: General Help
---

### Post by hunter_te on 2008-04-03
I was dual-booting. Winxp and ubuntu gutsy.

There was a 30 gig NTFS partition which i wanted to convert to ext3. 

I booted into XP installation CD. I deleted the 30 gig partition. I created a partition and removed the CD.

I put in Live Gutsy CD(although there was no need, but i realised after 30 seconds approximately), went to Gparted application, formatted that 30 gig partition with ext3, it was done within 10 seconds... :o
I hope its like that cos NTFS partitioning takes a long time.

Then i removed Live CD and booted with Hard disk.

Oh my god, XP is starting on its own. 

No boot select screen. Just direct booting into XP.....

I put in live cd to check if my linux file system is there....it is there...

I rebooted and rebooted and rebooted......to boot into XP all the time....

DAMMMMMMNN, i dont want to go through all that installation pain again....i had installed so many programs......i am messed up

PLEASE HELP.....

---

### Post by wieman01 on 2008-04-03
This is how you recover GRUB:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub")

---

### Post by sekinto on 2008-04-03
Could you post two things?

First your GRUB configuration file:
gksudo gedit /boot/grub/menu.lst

Second your fstab file:
gksudo gedit /etc/fstab

---

### Post by wieman01 on 2008-04-03
The OP cannot boot Ubuntu anymore... So posting these will be... well, impossible? Unless you boot from Live CD of course. But that's what the tutorial above is about.

---

### Post by hunter_te on 2008-04-03
Hello, thanks wieman for ur support..

I am unable to solve this...
Here goes 

> 
[B]Using the Ubuntu Desktop/Live CD
Quick Start[/B]




[IMG]http://img20.imageshack.us/img20/5548/88888mg3.jpg[/IMG]



As u can see in the image above, when i press tab it shows me that long list of possible commands...
and when i type find command, it cant find anything...

So that option didnt work.....

NOW

> **]From within Windows**

I downloaded and installed Unetbootin-supergrubdiskrev120 and rebooted

This was the first window....



[IMG]http://img217.imageshack.us/img217/7485/dsc02381ju4.jpg[/IMG]



I used to get this windows only when Vista and XP were installed....though now vista is deleted, i still get this stupid screen, never cared to find why...


Second Window on selecting Unetbootin-supergrubdiskrev120


[IMG]http://img90.imageshack.us/img90/4528/dsc02380mg5.jpg[/IMG]



First 2 options return to the same screen and here is the output of 3rd option...


[IMG]http://img90.imageshack.us/img90/8674/dsc02379bc3.jpg[/IMG]


I tried that 3rd option  4 or 5 times, and sometimes i got this screen too


[IMG]http://img356.imageshack.us/img356/4143/dsc02382ez5.jpg[/IMG]



In both above screens, it just hangs there. I gave 5 minutes wait for both screen, nothing happened....just my num,caps lock and scroll lights keep tinkling on and off and the screen gets weird pixels and hangs...



So that failed too...i booted into XP and uninstalled and installed again same soft again, but same problem.


NOW

> **Using the Alternate/Install CD and Overwriting the Windows bootloader**


I sat down to install...

This is how my partitions are.....


[IMG]http://img87.imageshack.us/img87/460/dsc02385wx0.jpg[/IMG]



And i changed that to this according to the guide



[IMG]http://img80.imageshack.us/img80/7997/dsc02386jb3.jpg[/IMG]


And this window below says it will format my drives......but the guide says dont format and back off but if i cancel it at that point, nothing changes........


[IMG]http://img230.imageshack.us/img230/8703/dsc02387yk1.jpg[/IMG]


Help

---

### Post by hunter_te on 2008-04-03
Now trying with this....

>  Using the Unofficial "Super Grub Disk"

---

### Post by hunter_te on 2008-04-03
Posting this from Ubuntu. Back to Life !! :P

---

### Post by wieman01 on 2008-04-03
Huu... Glad to hear it. It is very tough to give advice when one does not sit in front of the affected computer. Glad you made it on your own.

---

