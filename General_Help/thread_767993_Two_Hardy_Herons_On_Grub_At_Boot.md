---
title: "Two Hardy Herons On Grub At Boot"
date: 2008-04-26
forum: General Help
---

### Post by adouglasmhor on 2008-04-26
I looked around but I did not see this one anywhere so I took a Screenshot of my file browser for boot.

[IMG]http://img.villagephotos.com/p/2005-8/1070113/screenshotbootdoublerS.jpg[/IMG]

Link to a bigger shot (In case any of the rest of you are as old and blind as me :(

[http://img.villagephotos.com/p/2005-8/1070113/screenshotbootdoubler.jpg](http://img.villagephotos.com/p/2005-8/1070113/screenshotbootdoubler.jpg)

---

### Post by MobiusNZ on 2008-04-26
That happens when a new kernel is released. Instead of just over-writing with the new version (like with most other program updates) kernels are usually installed alongside each other, just in case you can't boot off the new one.

If you want to get rid of the older one, just use synaptic or apt-get.

---

### Post by adouglasmhor on 2008-04-26
Thanks I will leave well alone for now then, maybe clean it up in a week or two.

---

### Post by forestpixie on 2008-04-26
I would leave 2 in the menu - then if a problem occurs with one you can boot the other. I always leave 2 in my menu list.

Do you know that you can attach piccies - if you use the New Reply button or when you write a new thread there  is a attachment button on the text box toolbar looks like a paperclip.

---

### Post by sailor2001 on 2008-04-26
to remove older kernels when you are ready:  sudo apt-get purge linux-image -2-6-**-** generic

---

