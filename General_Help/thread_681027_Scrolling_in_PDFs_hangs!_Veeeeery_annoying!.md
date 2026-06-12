---
title: "Scrolling in PDFs hangs! Veeeeery annoying!"
date: 2008-01-28
forum: General Help
---

### Post by endre on 2008-01-28
Hey, I'm close to throwing my laptop out the window now, so I really hope you guys can help me out here!

I've got a problem with scrolling in pdfs and webpages - quite often it looks like the scrolling function just hangs, and it scrolls at hyper speed all the way to the bottom of the document/webpage. Being a student reading literally dozens of pdf files daily, this is becoming more than slightly annoying! Here I am, halfway through an article, and zooooom, I'm at page sixty something, and no idea where I was. Thank you, Ubuntu! :mad: Does anyone have any idea how to fix this?

I am using Ubuntu 7.10 (this was not an issue in previous versions)

All desktop effects enabled

I've got a 1,6 Mhz Centrino, 1 Gb ram.

ATI Radeon 9800 128 mb 

I've tried every pdf reader available, Adobe, Evince, etc and the problem is the same everywhere. 

  Thank you!

---

### Post by alexei.colin on 2008-04-17
I'm having trouble with scrolling in Adobe Reader as well. But for me the scrolling is very SLOW. When I scroll a bit using side of touchpad or the Thinkpad red pointer device, the Adobe becomes unresponsive (it shows how it slowly scrolls but the window is blocked). Sometimes upon scrolling the whole Xserver crashes (a logout occurs).

In my case it is a Compiz problem, maybe same for you (disable desktop effects and see). Under metacity scrolling is fine.

In Compiz, ld.linux.so.2 and Xorg each take 25% of CPU while slow scrolling is going on. 
In Metacity, ld.linux.so.2 takes 40% of CPU (Xorg's use is negligible), and scrolling is fine.

The problem does not exist in Document Viewer. I'm trying to find more info about this issue. Responses are super-welcome!

EDIT: Running Ubuntu 7.10 (2.6.24-4-generic) with fglrx 8.01 on Thinkpad T60.

---

### Post by endre on 2008-04-18
Sounds very familiar indeed - should mention that it also happens occasionally in large internet pages as well, for instance if I'm reading a long academic article on one page or a media rich newspage. Have been suspecting Compiz as well, but since I've gotten so attached to the wonderful effects (flipscreens until I die!) I've decided to stay with it, and hope that we can sort it out somehow.

---

### Post by Washer on 2008-04-18
[http://ubuntuforums.org/showthread.php?t=293904](http://ubuntuforums.org/showthread.php?t=293904)

---

### Post by alexei.colin on 2008-04-18
Washer, thank you for the link.
I do have the latest fglrx ATI drivers (v8.01) for my Radeon x1400.

---

### Post by russo.mic on 2008-04-18
This happened until I disabled AIGLX in xorg.conf, and just settled again on XGL.  

Sucks, but better than the alternative.

Russo

---

