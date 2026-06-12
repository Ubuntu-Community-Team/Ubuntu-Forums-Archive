---
title: "Blurred lines across screen Ubuntu 14.04"
date: 2015-12-17
forum: General Help
---

### Post by addlednoob on 2015-12-17
Hi All, 

After a while running my computer I get lines appearing across my screen. Ive included some screen shots to clarify. 

This happens in Unity, and also with Gnome-flashback. 

Seems to be more prevelant when Im running firefox with a bunch of tabs.

Im running a Thinkpad X61 with 3GB of RAM.

Any thoughts on how I might be able to clear this up? 

Its incredibly frustrating having to restart my laptop every half hour to get rip of this screen effect...

Thanks for your help..

.[ATTACH=CONFIG]266209[/ATTACH][ATTACH=CONFIG]266210[/ATTACH]

---

### Post by XBNCPRk on 2015-12-17
What video card/driver are you using?

If you dont know off the top of your head, you can find this by running ```
lshw -c video
``` After a few seconds of polling, there will be a section of data displayed listing the video card, clock, version, etc. Your card type will be listed and near the bottom of that block, on the line that says 'configuration...' it will list the driver currently in use.

---

### Post by addlednoob on 2015-12-18
Here the output;

  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f8000000-f80fffff memory:e0000000-efffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f8100000-f81fffff

---

### Post by mörgæs on 2015-12-19
Intel drivers have improved a lot during the latest releases. Do you see the same in a live boot of 15.10? 
X/Lubuntu are also worth trying.

---

### Post by nakiamiir on 2016-03-30
I've been having the same issue from Xubuntu 14.04.4 (Also tested with Xubuntu 15.04 and 15.10)
(HP Pentium 4, tried on 3 PCs with different HDDs and USB installers)

I currently have one that has Xubuntu 14.04.3 and the problem hasn't happened yet.

Any ways to fix the issue? Or, is it that some video drivers came out and broke it for me? :confused:

---

### Post by mörgæs on 2016-03-30
Hi, welcome to the fora.
Please run the same command as in #2 and post the results in CODE tags (unlike #3).

---

