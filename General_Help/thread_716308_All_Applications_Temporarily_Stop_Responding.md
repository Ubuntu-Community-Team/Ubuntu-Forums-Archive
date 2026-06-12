---
title: "All Applications Temporarily Stop Responding"
date: 2008-03-05
forum: General Help
---

### Post by fireman biff on 2008-03-05
Sometimes while using my computer all the open programs seem to stop responding. Typically I will be using a program that stops responding. I will then switch to another open program which usually accepts one or two clicks and then also stops responding. This will happen to any program I try to use until somewhere between 30s and 2m have passed and then all programs will suddenly start responding again. Any mouse clicks or typing I did during the freeze will then typically go through as if I only just did it. This also causes the panel to stop responding after a while.

During this freeze, if I have music playing it will continue to do so, but I am unable to change the song or adjust the volume.

I'm using Gutsy (with Gnome and Compiz). Programs I typically have opened when this happens include RhythmBox, Pidgin, Firefox/Swiftweasel and Nautilus. I have a swap partition of around 3GiB which is active, and 1 gig of RAM.

---

### Post by murataht on 2008-03-05
This means a program is running at the background, sucking up all the resources...

you should check with "top" command. it gives more details about which program is doing that. 
If you can't switch or click, maybe you should add a "system monitor" on the panel, and add "CPU" and "Memory" option to it (more if you want). this should enable you to observe the "CPU" workload and "Memory" usage.

I can make a wild guess, it is either because of a "memory to swap" operation or because of a CPU intense  program such as "treckerd". 

good luck.

---

### Post by fireman biff on 2008-03-08
I am not able to run top while the problem is happening so I added the system monitor to the panel as you suggested.

When the problem happened the system monitor stopped responding too, so the graphs weren't updating. When the system started responding again the graphs updated and were as follows:
Processor - jumped up about halfway and then immediately back to normal
Memory - no change
Swap - no change (lots of space available)
Load - increase slightly and stayed that way for a while (it was just over 2)
Disk - maxed out to 100% and then immediatly back to normal

I'm not sure what to do about this though. Any advice?

---

### Post by HermanAB on 2008-03-08
It may be a problem with HAL and the CDROM driver.

Unplug the CDROM and see if the problem goes away.

---

