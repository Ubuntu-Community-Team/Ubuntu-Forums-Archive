---
title: "i8kmon lag - Dell XPS 13 9333"
date: 2014-06-21
forum: General Help
---

### Post by $teve on 2014-06-21
Hi,

I recently bought a new XPS 13 9333 i5 and immediately installed Ubuntu Gnome 14.04. 

From the start I've had an issue with the fan not activating (it didn't work at all, even when the CPU went as high as ~75C). I installed i8kutils and followed this guide to configure it:  [http://keenformatics.blogspot.co.uk/2013/06/how-to-solve-dell-laptops-fan-issues-in.html](http://keenformatics.blogspot.co.uk/2013/06/how-to-solve-dell-laptops-fan-issues-in.html)

The fan is now working and seems to activate correctly based on the specified thresholds. However, I now have a very noticeable lag/stutter every so often, which is more apparent when playing music or watching videos :(

Last week I upgraded the BIOS to the latest version and all of the software is up to date.

Please, if someone can help it would be greatly appreciated.

Thanks.

---

### Post by $teve on 2014-06-23
Update:

I've been doing some more digging into this problem and it seems to have something to do with accessing the /proc/i8k file. 

I tested this by running cat /proc/i8k which causes the system to hang for a second and introduces a stutter in the system performance. 

I don't know where to go from here :-(

Please help.

---

