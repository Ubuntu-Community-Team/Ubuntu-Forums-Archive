---
title: "[SOLVED] wubi installation problem"
date: 2008-05-25
forum: General Help
---

### Post by knull on 2008-05-25
hi to all, i'm right now trying to install kubuntu through wubi on windows vista

i'll begin to explain..it just stops downloading at certain point during the download process

here is an image to illustrate:
[http://img98.imageshack.us/my.php?image=wubiinssg0.jpg](http://img98.imageshack.us/my.php?image=wubiinssg0.jpg)

i've tried twice now, same result it gets stocked and just stops downloading.
First time it stocked about 56%, second time it stopped about 85%(screenshot above) my internet connection its fine, it just don't finish downloading i've  been waiting already for about 6 hours help please

i'm very sorry about my bad english i know....
thanks to all in advance for your attention

---

### Post by Dave2k6 on 2008-05-25
Download kubuntu 8.04 iso manually from their website and save it into the same folder as wubi installer. The installer will then use the downloaded ISO instead of download one.

---

### Post by knull on 2008-05-25
hi, i tried placing the iso file inside wubi's folder and wubi completely ignores it and begin downloading the file, what can i do ? i'm now confused


thanks

---

### Post by ago on 2008-05-26
Wubi ignores an ISO in 2 cases:

* It is not the right ISO (must be 8.04 desktop CD)
* Its md5 is not correct (ISO is corrupted)

The log in your user temp folder will reveal the issue. Make sure there are no other ISOs in the way.

---

### Post by knull on 2008-05-26
there was my mistake, i tried with the alternate version "kubuntu-8.04-alternate-i386.iso" thank you both i really appreciate it, i'm now installing kubuntu :)

---

