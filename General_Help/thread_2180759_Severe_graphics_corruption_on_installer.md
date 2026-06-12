---
title: "Severe graphics corruption on installer"
date: 2013-10-14
forum: General Help
---

### Post by synaptix on 2013-10-14
Hi there. I have a Diamond HD6450 and I want to get back into trying Linux with it running the open source drivers. I have tried Ubuntu 12.04, 13.04 and 13.10 final beta on both a DVD and USB flash drive and this problem occurs.

I can see the first purple screen fine with the little icon at the bottom, but once the next part shows up with the Ubuntu name and loading dots all goes crazy.

Hardware is perfectly fine, since I'm using it on Windows at the moment. All MD5 hashes were checked and verified. All burns to DVD and USB were successful and write verification passed 100%.

Basically it goes from this:
[http://i.imgur.com/siCV4jm.jpg](http://i.imgur.com/siCV4jm.jpg)

To this madness:
[http://i.imgur.com/27l0lJA.jpg](http://i.imgur.com/27l0lJA.jpg)

---

### Post by synaptix on 2013-10-14
Solved, apparently my card needed nomodeset to be passed for it to work without graphics corruption. Got 13.10 installed now. :)

---

### Post by CalcProgrammer1 on 2013-10-14
What did the corruption look like?  I'm using Ubuntu GNOME 13.10 on my desktop with two Radeon cards and I'm getting corruption on the windows that looks like this:

[http://i.imgur.com/tp3Lw2H.jpg](http://i.imgur.com/tp3Lw2H.jpg)

Is that what you had?

---

