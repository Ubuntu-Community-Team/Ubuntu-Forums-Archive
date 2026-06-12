---
title: "How do I mount a special image"
date: 2008-01-08
forum: General Help
---

### Post by airali on 2008-01-08
Hello!
I've an NRG image (Windows Nero Format) of a DVD on my pc and I'm trying to mount it with my just installed Ubuntu v7.10.
How do I do?

I tryed reading something about this, but nothing worked, because the image has some "copy protection" stuff and doesn't get recognized by the os when mounted...

Any suggestions?!

---

### Post by steveo_mcg on 2008-01-08
Its a proprietary nero format so i doubt it'll be mountable from the loop back device, have you still got access to nero, can you convert it an ISO?

---

### Post by airali on 2008-01-09
Hm...I don't know if it is so necessary...
I found a software (AcetoneISO) which seems to be compatible with NRG image format.
It seems to succeed in mounting my image, but the "dvd" isn't recognized by the system...so I cannot play it :S
I think it's somehow related with DVDs copy protection....they are encripted...

What shall I do?

---

### Post by bulletxt on 2008-01-12
is it a dvd film?

open acetoneiso2 , go to "play tab" and just play it with kaffeine or vlc.

if it gives error, install libdvdcss package which is NOT in official repositories but here:

[http://www.debian-multimedia.org/pool/main/libd/libdvdcss/](http://www.debian-multimedia.org/pool/main/libd/libdvdcss/)

---

