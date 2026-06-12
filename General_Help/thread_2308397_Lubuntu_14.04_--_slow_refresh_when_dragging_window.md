---
title: "Lubuntu 14.04 -- slow refresh when dragging windows"
date: 2016-01-02
forum: General Help
---

### Post by rccharles on 2016-01-02
I'm experiencing slow windows refresh when dragging windows.  I can drag the windows faster then they will move.  When I stop dragging the windows will still be trying to catch up.  Lubuntu 14.04.  When running firefox, page up and down is slow.

I know I'm running on old hardware .. IBM T22 1ghz.  I do not notice performance problems running Windows XP.  [ I do notice all the "normal" windows headaches. ] Yet, I have a t20 700mhz with Fedora 19 where the windows move just fine. 

Any way of speeding this up?  What is different about Fedora 19 vs lubuntu 14.04 to cause this slowness?  

I'm looking for a light weight distro using lxde with the latest firefox.  Any light weigth distro where firefox is kept up-to-date, but the rest of the distro doesn't change?

Robert

---

### Post by ubfan1 on 2016-01-02
What's your video hardware?  A proprietary driver might be what you need to fix that performance problem.

---

### Post by Bucky Ball on 2016-01-02
*Thread moved to **General Help**.*

---

### Post by rccharles on 2016-01-03
```
gary@gary-desktop:~/screenImages$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0c)
00:03.1 Serial controller: LSI Corporation LT WinModem (rev 01)
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: S3 Graphics Ltd. 86C270-294 [SavageIX-MV] (rev 13)
gary@gary-desktop:~/screenImages$
``` 


I've attempted to attach 


But here is a picture.

---

### Post by Bucky Ball on 2016-01-03
The S3 Savage are very old and never worked well in Linux when they were new. I have one in an old desktop under my desk (which had a similar setup to your: S3, 1Gb of RAM). 

There is no tip or trick that I found which will make that thing work any better.

---

### Post by rccharles on 2016-01-03
Here is what is in my T20:
01:00.0 VGA compatible controller: S3 Graphics Ltd. 86C270-294 [SavageIX-MV] (rev 11)
works fine with Fedora 19.  I've been running it for two years now without any problem. I use my t20 as a display to my mac mini. 

Here is what is in my T22:
01:00.0 VGA compatible controller: S3 Graphics Ltd. 86C270-294 [SavageIX-MV] (rev 13)
[ I plan on giving it away.  Hate to have to say "use windows". ]
I'm pretty certain I had fedora running on this t22 ok.

I know the rev # seems minor, but could have a big difference too. 

Is there any way of figuring out what drivers Fedora 19 is using and coping them to lubuntu?   


I know IBM put a log of proprietary hardware in their machines.  audio isn't working either.

Robert

---

