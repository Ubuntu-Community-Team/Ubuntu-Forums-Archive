---
title: "I can't get my Sansa Clip connect to my Sytem."
date: 2008-06-07
forum: General Help
---

### Post by Ioky on 2008-06-07
I just bought a new Mp3 player The SanDisk Sansa Clip 4GB Silver, and yes, I do read over page after page, it do work under Linux. So after I bring it home from store, I plug it in to my system. But nothing shows up, I have no idea why. Not just that, it doesn't get get charge. I can't get it to mount at all. 

I search on this forums, some one said unplug and re-install the USB mouse helps or type "lsusb" help. I tried both, but I just can't get it to work. 

I can't get he player mount, and it doesn't charge while it connected. 

Anyone can help?

---

### Post by redonwhite on 2008-06-10
Hello,  Make sure the USB is pushed firmly into both the computer and especially the mp3 unit.  Because i was in the same boat as you and then i realized i didn't push the mini USB into the sansa clip all the way =).  Once i did it worked fine.  hope this might help buddy.

---

### Post by Ioky on 2008-06-10
Oh by the way, I get the problem fix, by typing 

 sudo rmmod ehci_hcd

in the Terminal

---

### Post by Halcyon31415 on 2009-06-28
Wow that totally worked for me too. What does that code do?

---

