---
title: "Screen flickers when running open gl applications with AIGLX and Compiz in Gutsy"
date: 2007-12-31
forum: General Help
---

### Post by awatts on 2007-12-31
Running ASUS f3ka with ATI radeon mobility 2600, currently using the latest drivers (8.44) however the problem has existed since at least driver version 8.4.  Basicially whenever i run an opengl game like ppracer or nexuiz or if I view opengl screensavers the screen flickers black.  If i run the applicatins in a regular session running X then all is fine and i have full 3d acceleration.  On my old laptop, before ati supported compiz and aiglx, i used XGL.
[this fix ]("http://www.getautomatix.com/forum/index.php?showtopic=133") allowed me to run 3d accelerated games with out changing sessions.  is there any way to do something like this with aiglx?

---

### Post by niallporter on 2008-01-04
> **awatts said:**
> Running ASUS f3ka with ATI radeon mobility 2600, currently using the latest drivers (8.44) however the problem has existed since at least driver version 8.4.  Basicially whenever i run an opengl game like ppracer or nexuiz or if I view opengl screensavers the screen flickers black.  If i run the applicatins in a regular session running X then all is fine and i have full 3d acceleration.  On my old laptop, before ati supported compiz and aiglx, i used XGL.
[this fix ]("http://www.getautomatix.com/forum/index.php?showtopic=133") allowed me to run 3d accelerated games with out changing sessions.  is there any way to do something like this with aiglx?

Have you got desktop effects enabled?  I just managed to get ATI drivers for my X800XL running for the first time and found i got the same thing as you describe but only with the wizzy 3D compiz stuff enabled.

It turns out it's got something to do with the X server rather than comiz or OpenGL or even (as I had assumed) the official ATI drivers.  I'm afraid I can't post a link because I'd bookmarked it on my GF's machine and can't find it now i'm back on my own but I did read this on a blog belonging to (I think) one of the freedesktop.org developers working on the X.org server.  I think I found the link either on this forum or an Ubuntu launchpad bug report relating to the same issue so you'll probably hit on it with a search or two anyway.

Bad news is doesn't sound like it's likely to be fixed until the next Ubuntu after 8.04, and that's assuming the X.org devs manage to implement it, I guess.

N

---

### Post by mj_ja55 on 2008-05-26
Thanks, turning off desktop effects fixed this problem for me.  I am using an ATI Radeon X1400 with drivers installed by Envy in Ubuntu 8.04.  This link ([https://answers.launchpad.net/ubuntu/+question/31908](https://answers.launchpad.net/ubuntu/+question/31908)) discusses this problem also.

---

