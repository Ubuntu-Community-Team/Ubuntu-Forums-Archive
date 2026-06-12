---
title: "Fullscreen game(s) only use part of screen"
date: 2013-07-19
forum: General Help
---

### Post by dwarft0ss on 2013-07-19
I have scoured google and various forums for days looking for an answer to this problem (read: didn't want to post a thread and wait!), apologies if it has already been posted somewhere.

When I install 12.10 Xubuntu from the CD and don't update anything, fullscreen games such as Uplink and Goonies just work as they should...everything else does too. However, after updating (251 files) some fullscreen games use only a portion of the screen, with the "working part" situated in the top left. I've added pics to show what I mean by this....

[ [IMG]http://s1.bild.me/bilder/260513/thumb_2751357100_1861.JPG[/IMG]]("http://www.bild.me/bild.php?file=2751357100_1861.JPG")

[ [IMG]http://s1.bild.me/bilder/260513/thumb_3204134100_1862.JPG[/IMG]]("http://www.bild.me/bild.php?file=3204134100_1862.JPG")

Some games, such as Half-Life work just fine. I think it might use a different method of rendering? Anyhow, I've looked into SDL and God knows what else as a cause, and I don't think the xorg intel drivers are causing this, but I honestly have no idea.

I've attached sysinfo output and pasted the relevant bits below (tried viewing the txt in windws and it was a jumbled mess). Any help will be greatly appreciated; I can restore a stock 12.10 clonezilla image but I'd like to be able to update -and- play games in proper working fullscreen!

Edit: I've tried installing 12.04 and 13.04 and both of those have this same problem, for what that's worth.


```
SYSTEM INFORMATION
    Running Ubuntu Linux, the Ubuntu 12.10 (quantal) release.
    GNOME: unknown (unknown)
    Kernel version: 3.5.0-36-generic (#57-Ubuntu SMP Wed Jun 19 15:11:05 UTC 2013)
    GCC: 4.7 (i686-linux-gnu)
    Xorg: 1.13.0 (08 October 2012  03:34:08PM)

CPU INFORMATION
    GenuineIntel, Intel(R) Pentium(R) M processor 1.73GHz
    Number of CPUs: 1
    CPU clock currently at 1733.000 MHz with 2048 KB cache
    Numbering: family(6) model(13) stepping(8)
    Bogomips: 3458.14
    Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est     tm2 

HARDWARE INFORMATION
MOTHERBOARD
    Host bridge
        Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 0944
    PCI bridge(s)
        Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
    ISA bridge
        Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
        Subsystem: Hewlett-Packard Company Device 0944
    IDE interface
        Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Device 0944

GRAPHIC CARD
    VGA controller
        Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])
        Subsystem: Hewlett-Packard Company NC6220
```

---

### Post by CatKiller on 2013-07-20
What resolution are you running the games at? If I try to fullscreen a game at non-native resolution I get that kind of thing because my monitor can't change mode to the lower resolution. It just uses the same resolution & displays on part of the screen. There might be a monitor or driver option to force scaling, or you could up the res of the game.

---

### Post by dwarft0ss on 2013-07-20
Hey thanks for taking the time to respond.

Well one game runs at 800x600, so it uses roughly a fourth of the screen when it is misbehaving as seen in pic. My monitor resolution is 1400x1050.

As an experiment, I installed a clone of 11.10 I had to the laptop. It upscaled fullscreen games just fine. It isn't a supported OS now, but it had updates for many thing including graphics drivers and a kernel update. I found that if I update everything -except- for the kernel and its related packages, my games would upscale and take up the whole screen as they should. Once I updated kernel it was back to what I showed in the pics. The offending files are shown in the pic below:

[ [IMG]http://s1.bild.me/bilder/260513/thumb_9908459graphics_screwed_culprits_xubuntu.png[/IMG]]("http://www.bild.me/bild.php?file=9908459graphics_screwed_culprits_xubuntu.png")

Updating the kernel is what borked it, pretty much (at least in 11.10, and likely in other later versions). If I install 12.10 from a CD without updating I am also able to play games properly there as well, and I'm willing to bet that updating the kernel there would cause this problem to resurface.

I've made another clonezilla image of 11.10 with everything working and the above waiting to be installed in update manager so I can keep testing different things. On a side note, updating to 12.04.2 LTS from this state made the game run oddly again as in the pic above (updated kernel likely?). 

Again, it appears that the kernel is behind this behavior. If only I knew what to tweak, if anything, to make games upscale and use the whole screen.

Edit: I never thought to look around google with the term "scaling". I found this...[it sounds exactly like my issue here (and is unsolved).]("http://askubuntu.com/questions/288198/lower-than-max-resolutions-not-scaling-to-full-screen")

---

### Post by mörgæs on 2013-07-20
Sounds like a regression. 
How does it work in 13.10?

---

### Post by dwarft0ss on 2013-07-30
Heh, wouldn't you know it....I make my first post here...report a few spammers....and BOOM, site is down. Darn the luck! Good to be back though.

I tried Xubuntu 13.10 and got the same issue with lack of scaling. As it stands I think I will stick with either 11.10 or 12.04.1 and just simply not upgrade them until I (we?) figure this out, if ever.

---

### Post by e-seiner on 2013-08-24
I have found a quick and diry solution.

I have try to play Starcraft in Xubuntu 13.04 and get the same issue. To solve it i have use the command: > xrandr --output LVDS1 --scale FOOxBAR. I need the resolution by my Monitor and the one by Starcraft. The Monitor resolution is 1200x800 and Starcrafts is 640x480. Now a little bit math: FOO=640/1200 and BAR=480/800. So i do this:  > xrandr --output LVDS1 --scale 0.5x0.6 and start SC. It only works with one number after dot, so "0.53" dosnt works! It is dirty because after playing you must restore: the original scaling with > xrandr --output LVDS1 --scale 1x1. 


I hope i find a better solution soon....

ps.:
I try to do > xandr --output LVDS1 --set "scaling mode" "Full aspect" play and then > xrandr --output LVDS1 --set "scaling mode" "None". It do the same but it shouldn't do the same!

---

