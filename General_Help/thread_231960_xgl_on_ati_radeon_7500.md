---
title: "xgl on ati radeon 7500?"
date: 2006-08-08
forum: General Help
---

### Post by honda on 2006-08-08
I have the default open source driver for the ati radeon 7500 and 3D acceleration is working good enough for eg. googleEarth and planet penguin racer (must be the last good ati card). I'd really like to try xgl, but the ati howto's seems to be talking mostly about the propriety driver that I can't nor need to use. I suppose I won't be able to use all the eye candy, but I think something should work since I obviously have working openGL support, right? Anybody tried xgl with that card? Or otherwise some educated guess if it could work? Mostly I'm concerned that I might mess things up so the rest of the family won't have a usable computer any more.

---

### Post by chaosgeisterchen on 2006-08-08
I suggest using AIGLX as it should be supported by your card.

---

### Post by honda on 2006-08-08
Really, I thought AIGLX was only supported on some intel cards.  Are there any howto's for AIGLX with my card?

---

### Post by chaosgeisterchen on 2006-08-08
[Working Cards for AIGLX](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL)

Here it stands.. HowTo can be found at ubuntuforums.org too

Here one for Intel-Card, but could be working for Radeon too
[HowTo](http://www.ubuntuforums.org/showthread.php?t=145068)

---

### Post by honda on 2006-08-08
Thank, you. I'll give it a try when enough spare time is found.

---

### Post by chaosgeisterchen on 2006-08-08
I give no proof upon my suggestion, but according to gentoo wiki it should work. Whether it works perfectly or not, one can only say upon testing it.

I forgot:

[readme](http://ubuntuforums.org/showthread.php?t=145068)

---

### Post by honda on 2006-08-08
Seems as the first link was really about XGL hardware support, but the AIGLX howto says that ati readeon is now supported, so I guess I have the option to try both... Anyway my understanding was that AIGLX needs updated drivers, and that's only possible for the open source ones, but that XGL could run on any old card with openGL support. Apparently the open ati drivers have now the needed tweaks to run also AIGLX.

---

### Post by chaosgeisterchen on 2006-08-08
Well.. you should read yourself through the differences of AIGLX and XGL.

XGL replaces the XServer while AIGLX is only based upon the X-Server as an addition AFAIK.

---

