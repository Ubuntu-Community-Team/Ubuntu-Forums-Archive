---
title: "Choppy streaming videos..."
date: 2012-12-31
forum: General Help
---

### Post by setemupknockem on 2012-12-31
I know that a bunch of these threads exist, but i have not been able to solve the problem on my laptop. Any type of streaming video be it youtube, linux, facebook, the video is choppy at full screen. I have dual-boot and these videos at full screen play perfectly fine on Windows XP.

I'm new to Linux, have a windows 8 computer and a mac. This laptop is old and is server/print server/ plus mini media center for my TV in the bedroom.

Using lubuntu 12.04 LXDE (older laptop that doesn't support PAE)

Laptop is the Sony VGN-A190
Centrino 1.7 GHZ
512MB DDR RAM (soon to be 1.25 DDR)
160 GB HDD
ATI Mobility Radeon 9700 - 64.0 MB

I have unchecked enable hardware acceleration in flash, tried in firefox and chromium, installed flash-aid in firefox. I think it has something to do with X.org display driver, but don't know exactly what I need to do. Again, very new to linux. 

I just want to lay in my bed and watch Hulu and Youtube lol.

Let me know what you need for me to run in terminal if you need more information

---

### Post by crispy_420 on 2012-12-31
My first guess would be lack of hardware specs. I know it works fine on Windows with the same specs but when Adobe did the Mac/*nix options they made them more CPU intensive. That may be your bottleneck. 

Bring up a system monitor and watch your CPU use top out.

Can't think of an easy fix for you, sorry.

---

### Post by Mark Phelps on 2012-12-31
The problem is likely to be that XP has good video drivers but Ubuntu is using the default open-source Radeon drivers -- because AMD dropped Linux driver support for that chipset years ago.

If you were running an older version of Ubuntu, one that still had ATI driver support, you would probably then see the same video performance as you do in XP.

---

### Post by Calinou on 2012-12-31
Find websites that use HTML5 instead of Flash (Youtube does, but for some videos only, see youtube.com/html5). Problem partly solved as flash eats CPU like hell.

---

### Post by setemupknockem on 2012-12-31
Thanks for the information.

Checked out CPU usage when using Flash and yes it goes up to 99%. Checked out youtube.com/html5, watched a video in html5 and plays way better. 

Guess I will have to go into XP to watch HULU.

---

