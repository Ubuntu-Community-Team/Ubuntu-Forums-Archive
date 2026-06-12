---
title: "memory test failure"
date: 2014-04-21
forum: General Help
---

### Post by debroos on 2014-04-21
Hi

I've just re-installed 12.04 via wubi on an Asus eeepc, following two aborted attempts to upgrade to 14.04.  Now the system runs much slower than before, most noticeably on streaming video which tends to be out of sync, where before the re-install I had no problems - it was all very smooth. I have the same apps installed as before - ubuntu restricted and the extra chrome codecs.

 I ran a system test which came up with this ... [FONT=Ubuntu Mono]"memory/info ~ FAILED ~ Runtime error (func=(main), adr=17): Divide by zero usr/share/checkbox/scripts/memory_compare: line 23: -3: substring expression < 0".  

I suspect that whatever this is indicating is the root of the problem, but I haven't a clue what it means or how to address it.  Any help will be very much appreciated.   [/FONT]:)

---

### Post by mörgæs on 2014-04-21
Wubi is deprecated, and it's better to run a real dual boot. 

Besides, I would suggest X/Lubuntu for an eee. How does 14.04 work in a live boot?

---

### Post by debroos on 2014-04-22
Thanks very much for that advice.  I'll check a live cd boot of 14.04

---

### Post by Topsiho on 2014-04-22
I agree with mörgæs that you should try Lubuntu or Xubuntu. I have an Acer Aspire One, on which I run Lubuntu, and though it runs not that fast, it is quite usable. While with the latest versions of Ubuntu it runs really uncomfortably slow.
I like Lubuntu less then Xubuntu, but that is only my personal opinion. YMMV.

Topsiho

---

### Post by Topsiho on 2014-04-22
I forgot: why did you call this thread the way that you did :)

Topsiho

---

### Post by debroos on 2014-04-22
!4.04 on a live boot appeared ok, unlike the update and the install from cd, both of which had failed with [COLOR=#000000]reports of serious disc errors, font errors - root file system check failure...[/COLOR]  This latest live cd boot wouldn't play mp3 files, but I hadn't installed the codecs that I have installed for 12.04.  I fired up system tester to check it all out.  It took forever to get started and hung after the sound test, which made no noise.  I gave up after waiting around 5 minutes.  

Xubuntu looks interesting.  I'll give it a whirl.  Easypeasy is recommended for eee pc range, but I don't get the impression it's up to date.   This thread was named in the wake of the memory test failure outlined above, which I thought might be connected to the slower performance of the reinstalled 12.04.  Prior to the 14.04 debacle, the pc went faster than it ever had with XP.

---

