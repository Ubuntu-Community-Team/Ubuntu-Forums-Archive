---
title: "Grub screen visual &quot;corruption&quot; and glitches"
date: 2018-03-05
forum: General Help
---

### Post by Melhisedek on 2018-03-05
I installed Ubuntu and everything seems to work but there is some weirdness going on on grub screen. It seems there are two screens displaying at the same time. Higher resolution purple and low resolution black.

Here is the screenshot as well

[[img]https://s18.postimg.org/98okltjvp/20180305_183953.jpg[/img]](https://postimg.org/image/98okltjvp/)

All the menus work and I can get into Windows and Ubuntu no problems but it looks really wrong

---

### Post by andy106 on 2018-03-05
Same here,Ubuntu 17.10,radeon driver
Nasty artifacts and lagging on grub menu (after updating grub to latest version "2.02~beta3-4ubuntu7.2_amd64")

Can revert grub to previous version??

---

### Post by again? on 2018-03-05
The fix [HERE]("https://ubuntuforums.org/showthread.php?t=2386182&p=13745234#post13745234") worked for me in Xubntu 17.10.
Search in file for "terminal_output --append" . Was line #270 here.
Apparently it has been fixed but I have no update yet.

---

### Post by andy106 on 2018-03-06
> **guber2 said:**
> The fix [HERE]("https://ubuntuforums.org/showthread.php?t=2386182&p=13745234#post13745234") worked for me in Xubntu 17.10.
Search in file for "terminal_output --append" . Was line #270 here.
Apparently it has been fixed but I have no update yet.

Work perfect,thank you!

---

