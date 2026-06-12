---
title: "Ubuntu 15.04 extremely slow"
date: 2015-08-16
forum: General Help
---

### Post by kiraq on 2015-08-16
Since upgrading to Ubuntu 15.04, my computer now runs extremely slow, and not just online. To get pages to load online, I usually have to wait till it times out, then refresh the page to have it load. So far it has been impossible to watch any videos online, because the buffering goes on for over an hour on a 15 minute video (ie: Youtube). I find myself downloading videos just to be able to watch them, but it usually takes several tries to finish a download.

 Off line I get text files and images that take several minutes to load, and sometimes I get grey-screens that just stick around until I force them to close (if it even allows that) or I hard reboot. Videos tend to freeze or buffer, and DVDs do the same, and sometimes the program just shuts down when there is a non-responsive screen. I have an almost new Asus that I bought new this year, so it's not an older computer. I'm not duel booting (I tried that, but Windows 8 prevented Ubuntu from opening). I had 14, and had no problems with that at all. I've tried some of the fixes I could find online, but nothing seems to work. I'm almost to the point of dumping 15 and putting 14 back on, even though there are no updates.

---

### Post by Vladlenin5000 on 2015-08-16
14.10 is EoL -> Do NOT use it. Indeed, it has no updates.
15.04 is the latest "stable" version and supported until January.
14.04 LTS is supported until April 2019.

So, your options are only the last two.
Now, your issue. What graphics card/chip do you have? If nvidia or AMD, did you installed proprietary drivers? If so, which version?

---

### Post by kiraq on 2015-08-17
As far as I can tell, it's not nvidia or AMD. ( I have the proprietary drivers activated) This is what I could pull up:
                                                                            
VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e)
 
 
 lspci | grep -i --color 'vga|3d|2d'
 
 
 00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e) (prog-if 00 [VGA controller])
     Subsystem: ASUSTeK Computer Inc. Device 14dd
     Flags: bus master, fast devsel, latency 0, IRQ 92
     Memory at d0000000 (32-bit, non-prefetchable) [size=4M]
     Memory at c0000000 (32-bit, prefetchable) [size=256M]
     I/O ports at f080 [size=8]
     Expansion ROM at <unassigned> [disabled]
     Capabilities: [d0] Power Management version 2
     Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
     Capabilities: [b0] Vendor Specific Information: Len=07 <?>
     Kernel driver in use: i915

---

