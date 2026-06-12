---
title: "Ubuntu freezing intermittent"
date: 2008-02-19
forum: General Help
---

### Post by Ramptu on 2008-02-19
Can someone help me figure out what is causing my intermittent freezing? I have Ubuntu 7.10 dual booting with windows xp. Everything seems to be fine except for a small problem I have with my refresh rate changing when using 1680x1050. My freezing problems may be related to my video problem but I don't enough about linux to work through this.

I'm using HPa1430n AMD 64 with integrated nvidia geforce 6150le
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00607960&lc=en&cc=us&dlc=en&product=1843642](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00607960&lc=en&cc=us&dlc=en&product=1843642)

My monitor is Viewsonic vx2235wm 22" lcd. 1680x1050@60Hz max

My refresh rate will change on its on. Things will start to look washed out and blurry as if I had fingerprints on the screen. Now sometimes I can go back to previous refresh rate other times when I do it doesn't actually change.

When I do nvidia-settings I set it at 1680x1050@60 and everything looks ok. It usually has the correct setting. Its the settings in gnome or compiz that change (and dont allow a 60Hz setting). there are 3 places where I see resolution and refresh rate can be set in Ubuntu (not including nvidia-settings), could these be conflicting? Which setting matters? 

If I reboot everything is usually fine. If I go to terminal and nvidia-settings my screen will adjust to the setting I have put into nvidia (like contrast,gamma ect.). Why does it take for me to open up nvidia-settings for this to happen. I think that something is not loading right. This may or may not be related to my brief freezes (lasting from 5-10 seconds) where all I can move is my mouse. My freezing always seems to free itself as if something were happening in the background and later does its thing and frees up.

I have looked at my logs but I don't have a clue as to what I'm looking at. I can't tell what is a normal function or some background process hanging up. If someone can just look at my settings and logs I'd appreciate it.

Let me know what to post and I will, let me know how to post what you need. I'm loving Ubuntu but this freezing and resolution problem is driving me nuts.

---

### Post by Ramptu on 2008-02-20
Researching this problem I came across this:

 MP-BIOS bug: 8254 timer not connected to IO-APIC

during my boot up sequence. It occurs very quickly and I had been ignoring it because I thought it was related to the OS boot selection menu. But it appears its related to IRQ maybe? This would explain whycompiz locks up and sound still plays and mouse still moves.

Am I looking in the right direction here? Anyone have any experience with this?

---

### Post by photismos on 2008-02-22
I'm very new to Linux, but I was having very similar errors....random freezing (even restarts at times) but usually still able to use my mouse, although to no avail since nothing was selectable, and of course the keyboard was completely useless (frozen)...nothing worked. It was happening intermittently, wondered if it was Firefox or my movie player or my NVIDIA driver something I was doing...NOT SO!  

I searched a few threads here and found that editing "/boot/grub/menu.lst" adding just two little words..."noapic nolapic" fixed it COMPLETELY. Since then I've had no freezes at all.

Here's where the those "words" went in the context of my menu.lst, if it helps you to know where to put it:

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-rt
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-rt root=UUID=56ef75eb-5ce9-4863-a4ee-2d4d2a167847 ro noapic nolapic quiet splash
initrd /boot/initrd.img-2.6.22-14-rt
quiet

...AND that's it. you put it in that "kernel" line and restart. Hope it helps. If it does, would be nice if you confirmed that for others... =) That's what I'm doing...trying to find the original thread(s) I found this solution in to confirm it works! =D ...well, again...hope it helps!

---

