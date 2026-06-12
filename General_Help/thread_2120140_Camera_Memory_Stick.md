---
title: "Camera Memory Stick"
date: 2013-02-25
forum: General Help
---

### Post by briar rabbit on 2013-02-25
Hello,

I recently got a sony handycam.  The "Memory Stick" for it is not recognized by my Ubuntu 10.04.  This "Memory Stick" looks similar to my Casio Camera 'SD Card' which works fine.

I went into Synaptic Package Manager and downloaded "libchipcard-ctapiO" which is 'library for accessing smartcards' made no difference.

Before that I found "sudo add-apt-repository ppa:relan/exfat"
which someone used to get their "SD card" to work.  Did not work!

All my searches here for "Memory Card" have returned USB related results.  

Can someone tell me how to fix this.

The card is recognized by my neighbors 'other' OS.

thank you

---

### Post by eddier on 2013-02-25
Are you trying to read it using a card reader? I had the same problem with my sony DSLR camera-all I had to do was leave the card in the camera and connect with a USB cable that had a mini USB plug on one end.
Most of the Handycams as far as i can discover have a built in USB cable.

eddie

---

### Post by briar rabbit on 2013-02-26
Thanks eddie,

That is the long way around in my opinion - but that did it.

I will mark this solved.

Thanks again for the help.

---

### Post by coldraven on 2013-02-26
Your card reader probably cannot read SDHC cards, time to buy a new one :p
[http://en.wikipedia.org/wiki/SDHC](http://en.wikipedia.org/wiki/SDHC)

---

