---
title: "Slow sound, low speed"
date: 2006-10-22
forum: General Help
---

### Post by hamil on 2006-10-22
Hello guys!

I did an upgrade of xinit, gnomebaker and some language-pack files this morning. After this upgrade, all my music and movie files, plays the sound in a relly slow manner. It is like the speed on the soundfiles has been reduced to something like 50%...
It does not matter what kind of application I open the files in, it ends up playing it really slow anyhow. In XMMS, I even tried to change from ALSA to esd, just to see if anything changed, it did not... 

Everything have worked fine, until this morning. And I have NOT changed any configuration files whatsoever these last days..

I also did try to restart alsa, without any results..

Any help would be highly appreciated!

Lasse

Edit:
Well, I have now tried to downgrade both xinit and GnomeBaker, but still the same issues with the sound... I really need help on this one... (And this issues is on my 6.06 machine, NOT 6.10..)

---

### Post by hamil on 2006-10-23
*Bump...

Still have not been able to fix this..

Have even rebooted the whole computer, but still no luck..

Please help me...

---

### Post by tehwa on 2006-11-19
Hi, I've had this problem for weeks, and just had some success running this command:
```
alsactl restore 0
```Where '0' is the card number (verify with aplay -l).

This restored sound to its usual 'speed'.

Hope this helps.

---

### Post by hamil on 2006-11-19
Thanks!

Will keep that in mind, if the problems comes up again. I did a clean install of 6.10 on that machine eventually. 

Funny that no one else has been bothered with this.. And I do not understand why it happened.

---

