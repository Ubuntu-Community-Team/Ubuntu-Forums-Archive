---
title: "Installing Grub and getting off blackscreen"
date: 2014-06-20
forum: General Help
---

### Post by Vyivrain on 2014-06-20
Hello, there is much information on the i-net how to install grub and so on, but... not when you have a blackscreen to accompany with. My problem looks like this, earlier I posted a thread about "wifi not working on ubuntu 14.04" , that was because ubuntu has a bug with my wifi adapter, so I was told to return to stable version 12.04. So I deleted ubuntu with windows disk partition and grub from this tutorial [https://www.youtube.com/watch?v=KV84OabGB08](https://www.youtube.com/watch?v=KV84OabGB08). And after that fun happened. I installed ubuntu 12.04, grub didn't come out and windows started loading. After that I tried to launch from live cd "install ubuntu" or "try ubuntu" and after that I get blackscreen( while ubuntu was installed ). When I again tried to delete ubuntu and run live cd, it startes ok. And things cycle in that order. Can you advice something that I can get out of this uroboros? I thought about installing grub with "try ubuntu" at first, but I don't know if that's possible( I tried running sudo from trying an ubuntu and nothing good happened ).

---

### Post by oldfred on 2014-06-20
What system and probably what video card?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

 
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by Vyivrain on 2014-06-20
[COLOR=#000000]"What system?"[/COLOR]
Well I'm currently on Windows 8 , tried to install Ubuntu 12.04. Video card nvidia 740m, hd graphics 4000 intel - integrated. The last link I tried, but when I change to nomodeset Ctrl + X doesn't work, ubuntu says you can also save with F10 , but then windows starts booting.And I don't know if it matters but I had much more less code in grub menu edit( again looking at link 3 ).Again refering to the third link , the little guy doesn't come out so the first paragraph is not my problem , 2 is not too, because I could install ubuntu at least once and run it properly.Concerning first two links I'll try to test them.

---

### Post by oldfred on 2014-06-20
What brand computer and model. Issues vary a lot. 
With dual video you may be booting with either Intel or nVidia. And with UEFI you only get grub menu:

 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

If booting with Intel you usually need different boot parameters than nomodeset. See ubfan1's link above for some that may work.

But you will do a lot better with 14.04. Intel made many changes to kernal, support software and video driver that are only in 14.04. And UEFI works a lot better with 14.04. While you may be able to get 12.04 to work as its point release has been updated to be essentially 13.10 based, but I think resolving WiFi issues may be easier, but have not dealt with those. There are a lot of threads on various wifi chips and what driver is required.

      
 Broadwell (future) fix for use with 14.04's 3.13 kernel. Fixes really in 3.15 kernel
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY](http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY)
Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)

---

### Post by Vyivrain on 2014-06-21
In the end I was too lazy to read all that threads, so I reinstalled ubuntu 14.04 and we had mutual love( it installed without any problems ), as any pair we had quarrels ( f.e. unity flown away, keyboard driver didn't work ). But wi-fi still doesn't respond to my sincere calls. I thought that I could install ralink drivers and never mind the adapter, because on windows the driver that is responsible for wi-fi is also ralink. And about model and computer I'm on Asus X550VB.

---

### Post by oldfred on 2014-06-21
Several other Asus threads.

 Asus ASUS D550MA-DS01 - 14.04 only Ubuntu
[http://ubuntuforums.org/showthread.php?t=2223928](http://ubuntuforums.org/showthread.php?t=2223928)
 Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)
[http://ubuntuforums.org/showthread.php?t=2208852](http://ubuntuforums.org/showthread.php?t=2208852)
[http://ubuntuforums.org/showthread.php?t=2184383](http://ubuntuforums.org/showthread.php?t=2184383)
ASUS Zenbook UX301LAA ultrabook under Linux  - reboot, power issues
[http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTQ)
 ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1)
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)

---

