---
title: "Freeze then Crash"
date: 2006-11-09
forum: General Help
---

### Post by Zenlike on 2006-11-09
I'm new to Linux so please forgive my ignorance.

Unfortunately my computer keeps freezing. The mouse will stop responding - some times I can still use the keyboard. If I try and restart the x-Server (Alt-Backspace) it will hang the system. Othertime the keyboard stops responding as well. I'm forced to physically turn the computer off. 
Initially I did a clean install of Drapper - and had the same problem, I upgraded to Edgy and it still happens. Currently I am using a clean install of Edgy, It most often freezes in Firefox, but has frozen in other programs. Some times it will happen virtually as soon as I turn on the PC other times not at all.

I have tried useing both the Open source and close source Nvidia drivers and it happens with both.

NVIDIA Driver Version: 1.0-9629
Server Version Number: 11.0
Server Vendor String: The X.Org Foundation
Server Vendor Version: 7.1.1 (70101000)

I've also installed Beryl and it happens both with Beryl on or off.

I have just brought a new computer:

CPU: (Sckt775)Intel® CoreT 2 Duo E6600 CPU @ 2.4GHz 1066FSB 2x2MB L2 Cache 
CD: SONY DUAL FORMAT 16X DVD±R/±RW + CD-R/RW DRIVE DUAL 
HDD: 300GB SATA-II 3.0Gb/s 16M Cache 7200RPM Hard Drive
MOTHERBOARD: Asus P5N-SLI nForce 570 SLI Chipset LGA775 Supports Core 2 Duo CPU FSB1066 DDR2/800 Mainboard w/GbLAN,USB2.0,IEEE1394&7.1Audio
MEMORY: 2GB (2x1GB) PC6400 DDR2/800 Dual Channel Memory (Corsair XMS2 Xtreme Memory w/ 
SOUND: HIGH DEFINITION ON-BOARD 7.1 AUDIO
GPUs: GeForce 7900 GS (GPU 0)

uname -a:

Linux jerry-desktop 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux

I have set-up a dual boot on my PC - and XP seems to be working properly so I don't believe their is anything physically wrong with my hardware.

Any help or suggestion would be very much appreciated.

---

### Post by Morientes on 2006-11-18
I have the same problem! Please, does anyone know what can be done?

---

### Post by pkslot on 2006-11-18
Same problem here. I have noticed that when ever i'm using Firefox 2.0 there is a problem. Also when my Rhytmbox is playing the whole system becomes unstable.

When i'm using Opera instead of Firefox, there seems to be no problem at all.

I'm using Edgy eft, upgraded from the beta release.

---

### Post by dlehman on 2006-11-26
I have a similar but slightly different problem.  I upgraded my machine from darper to edgy with no problems yet.  so I proceed to upgrade my mom's computer from darper to edgy as well now she says when she is in the middle of a game the computer freezes or when she switches games the panels disappear.  She is not running Firefox and they are not intensive games they are the default games snake race solitaire, five or more etc.  

I tried an alt+F2 to run some apps to no response I tried restarting X ctrl alt bk space and it hangs.  I did and alt F1 to get console and it was giving errors about disk I/O however I have not been able to get it to recreate that error.  also in the console when I tried to login I enter username and instead of asking for password it would wait 5-10 sec. and ask for username again.  

I am running disk tests to make sure it is not hardware related but why would it work fine with darper and act like this with edgy?  

any suggestions would be greatly appreciated

---

### Post by dlehman on 2006-11-29
I did a surface test on the hard disk and came up with severl bad blocks is there nay way to get ubuntu to ignore the bad blocks and just use the good portion of the disk I also got the error 

failed to execute child process /usr/game/kpat (input / output error)

I think that means it is having trouble with the hard disk?

any help??

Thanks

---

### Post by cactaur on 2006-11-29
This also happens to me, but it's a total freeze, and I get no response from the computer, not even num lock. And for me, it seems to be random.

EDIT: Hmmm.....There might be a connection w/ firefox for me, because it happens when I use Firefox or Liferea.

---

### Post by Tom H on 2006-11-30
at least some people get someplace.  I get to sign on screen (1 out of every 10 reboots) most of time it locks on the blank screen prior, no keyboard, no mouse and ONLY way out is power off.  I am STILL looking for ideas and have tried different burns on 6.06 and 6.1 and both are same.  Trying to get it running on 500 meg gateway with 384 meg of ram and 60G hd nothing else on it but linux.

Tom

---

### Post by Elimist on 2006-12-01
Same problem here.
Complete freeze up. No keyboard, no mouse. Nothing. Usually when I'm running GAIM or Amarok, sometimes whenever though.

Hardware:
Graphics - Nvidia GeForce 7300 GS
Harddrive - Maxtor 80gb SATA
Motherboard - MSI RX480
CPU - Athlon 64 3200+

---

### Post by skale on 2006-12-04
I had the same problem.  Go to Preferences -> Power management and change all the "Blak Screens" to "Suspend".  Far from ideal solution, I know.  I don't know why screen blanking locks up X.  I want to say it is a bug, but it could be us doing something stupid.  Also, I am using Dapper, so it might be a different problem.  What the hell, try it, and see if it works.

---

