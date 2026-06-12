---
title: "Banshee - meet mr uninstall!"
date: 2008-05-11
forum: General Help
---

### Post by wookietim on 2008-05-11
I cannot get the new 1.0 version of Banshee to install! I try the software installer in Ubuntu and I get the 0.13 version. I try the steps outlined on the banshee site and I get... the 0.13 version.

I give up, Rythmbox at least works.

---

### Post by Joe of loath on 2008-05-11
have you tried:

sudo apt-get install banshee

---

### Post by wookietim on 2008-05-11
Yep - and guess which version that installs? You got it - version 0.13. I used to really like Banshee - but it will no longer recognize my MP3 player... And nothing I do will budge it out of that 0.13 ghetto

---

### Post by lswest on 2008-05-11
> **wookietim said:**
> Yep - and guess which version that installs? You got it - version 0.13. I used to really like Banshee - but it will no longer recognize my MP3 player... And nothing I do will budge it out of that 0.13 ghetto

getdeb.net has 0.99.1 or so: [http://getdeb.net/app/Banshee](http://getdeb.net/app/Banshee) just download & double-click

---

### Post by wookietim on 2008-05-11
My god - that worked great! Thank you a million times!

---

### Post by itsjustarumour on 2008-05-11
> **lswest said:**
> getdeb.net has 0.99.1 or so: [http://getdeb.net/app/Banshee](http://getdeb.net/app/Banshee) just download & double-click

Thanks for that.  I tried to install 0.99.1 Hardy deb last night from the Banshee PPA and got a dependency error (sorry can't remember what it was) but when I checked in Synaptic the relevant dependency was already installed so something was going very wrong there...

---

### Post by wookietim on 2008-05-11
Of course, this version, even though it sees my player, is still useless to me - every time I try to subscribe to a podcast it crashes Banshee...

---

### Post by lswest on 2008-05-11
> **wookietim said:**
> Of course, this version, even though it sees my player, is still useless to me - every time I try to subscribe to a podcast it crashes Banshee...

well, it is still in Beta, maybe they'll fix that in the real release?  i have a sandisk mp3 player, so i can't help you much with banshee, since i just manage it with whatever i have at the moment.

---

### Post by MaxCharge on 2008-05-12
Please fix your broken packages. Podcast support should never have been enabled.

[http://gburt.blogspot.com/2008/05/banshee-podcast-support-coming-in-beta.html](http://gburt.blogspot.com/2008/05/banshee-podcast-support-coming-in-beta.html)

Secondly, just use the PPA for banshee. There is no need whatsoever for these duplicate packages. It's hard enough getting the PPA packages right without having to chase down other unofficial packagers.

[https://launchpad.net/~banshee-team/+archive](https://launchpad.net/~banshee-team/+archive)

---

