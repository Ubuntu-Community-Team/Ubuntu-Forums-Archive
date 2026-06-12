---
title: "suspend and hibernate still don't work on my Dell E1705 laptop"
date: 2007-04-29
forum: General Help
---

### Post by SnowPunk98 on 2007-04-29
No matter what I try I can't get it to work, using a Nvidia card so the ATi hack won't work. Has anyone had any luck with this or know how I can get it working correctly?

---

### Post by SnowPunk98 on 2007-04-30
bump

---

### Post by SnowPunk98 on 2007-05-01
Should be the same issue with the E1405 and E1505

---

### Post by SnowPunk98 on 2007-05-05
bump

---

### Post by Talon2 on 2007-05-06
> **SnowPunk98 said:**
> bump

Not a fix but some info that might be useful:

In one of my boxes here I had a nVidia 7600gs AGP card using the nVidia driver.  I simply was not able to make suspend and hibernate work.  I searched here and in launchpad but only found confirmations, no solutions.  I happened to have an extra old ATI 9600.  I installed the ATI which uses the open source radeon driver.  3d works well (desktop effects) and so does suspend and hibernate.  I also have boxes with Intel graphics, another ATI (9250) abd a S3 chipset...suspend and hibernate work well.

My conclusion:  Something in the nVidia provided drivers is breaking suspend and hibernate.

That nice 7600gs card would like to find its way back into one of my boxes at some point.  I hope this problem is fixed soonest.

You might search launchpad or even the Linux forum at the nVidia web site.  If you don't find a duplicate you should report the problem.

---

