---
title: "resentful of ubuntu"
date: 2014-01-24
forum: General Help
---

### Post by odee2 on 2014-01-24
Hi people, till now i solved already many things from i was confused, but i must start explain what is my problem from beginning. So: I had 32bit ubuntu latest LTS version. Before i had XP and i played Counter Strike.
Started first problem... at 32bit ubuntu ATI RV370 is no restricted drivers and also from ubuntu software source is opensource driver bad, because counter strike will not start. After month of browsing on many forums and plenty of many types of resolution errors i found one forum, where one man maked a driver for ATI RV370, but is just for 64bit ubuntu. OK... So i formatted my HDD and maked fresh install of 64bit latest LTS version of ubuntu. My bad... i forget where was the driver, so again 10days with screen mistakes i found i dont know where :) a similar driver. YEAH, Counter Strike startiiiing without error, but when i tried playing I got a cold shower again. FPS? 1 after 10 seconds.
NOOOO :( ok, without CS and gaming i can live...
I will make a music. LMMS at 64bit will not working. AT same machine with 32bit without problem.
After sucesfull install from ubuntu software center i can not find lmms. I can run it just from terminal but again probem... where are sounds? nowhere :( ok... ubuntu will be for me just for wem email. Again resolution is just 1024x768... at XP was 1280x1024 at my DELL LCD monitor and again with plenty of resolution errrors i gived up :(
My hardware is: intel core 2 CPU 6600 @ 2.40 x2, 1GB RAM, 4GB swap, 80GB HDD,
graphics driver: Gallium 0.4 on llvmpipe (LLVM 3.2, 128 bits)
lspci -nn | grep -iE "(vga|graphics)"
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300] [1002:5b60]
glxgears
1879 frames in 5.0 seconds = 375.692 FPS
2035 frames in 5.0 seconds = 406.915 FPS
1892 frames in 5.0 seconds = 378.340 FPS
2040 frames in 5.0 seconds = 407.992 FPS
1934 frames in 5.0 seconds = 386.741 FPS
2050 frames in 5.0 seconds = 409.903 FPS
glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9
NOW IS YEAR 2014 people. How can it be that ubuntu have so big mistakes?
and this day again.... i oppened the terminal an i added:
sudo su, password, apt-get autoclean, apt-get autoremove, apt-get update, apt-get upgrade
(I make this every day), and after one week i got error when i added apt-get upgrade
187 MB sa stiahlo za 18 min 37 s (167 kB/s)                                                   
(&#268;íta sa databáza ... momentálne je nainštalovaných 273014 súborov alebo adresárov.
Pripravuje sa nahradenie libjack-jackd2-0:i386 1.9.8~dfsg.1-1ubuntu2 (pomocou .../libjack-jackd2-0_1.9.8~dfsg.2-1precise1_i386.deb) ...
Dekonfiguruje sa libjack-jackd2-0 ...
Rozba&#318;uje sa náhrada libjack-jackd2-0:i386 ...
Pripravuje sa nahradenie libjack-jackd2-0 1.9.8~dfsg.1-1ubuntu2 (pomocou .../libjack-jackd2-0_1.9.8~dfsg.2-1precise1_amd64.deb) ...
Rozba&#318;uje sa náhrada libjack-jackd2-0 ...
dpkg: chyba pri spracovávaní /var/cache/apt/archives/libjack-jackd2-0_1.9.8~dfsg.2-1precise1_amd64.deb (--unpack):
 './usr/share/doc/libjack-jackd2-0/buildinfo.gz' is different from the same file on the system
Nezapíše sa správa apport, pretože už bol dosiahnutý limit MaxReports
                                                                     dpkg-deb: chyba: podproces vloži&#357; ukon&#269;ený signálom (Prerušená rúra)
Vyskytli sa chyby po&#269;as spracovania:
 /var/cache/apt/archives/libjack-jackd2-0_1.9.8~dfsg.2-1precise1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Can anybody help with that?

---

### Post by Bucky Ball on 2014-01-24
*Thread closed for moderation.*

---

### Post by Elfy on 2014-01-24
This thread will remain closed.

I suggest you read this [http://ubuntuforums.org/showthread.php?t=1422475&p=8920811&viewfull=1#post8920811](http://ubuntuforums.org/showthread.php?t=1422475&p=8920811&viewfull=1#post8920811)

and then start again - without the trolling title and seperate thread for each issue.

---

