---
title: "Any way to test restricted video driver in a Live CD session?"
date: 2007-09-13
forum: General Help
---

### Post by mjpatey on 2007-09-13
Interesting quandary... I'm running the Gutsy Tribe 5 Live CD, and am trying to get a feel for whether I should upgrade.  A big part of what I want to test is how well the nvidia restricted driver for my card (the 6200) works.

So I install the nvidia-glx driver in my live CD session... and of course, to enable it I have to reboot.  I dutifully reboot, but suddenly realize during shutdown that of course it's all going to be gone once I'm back up again.  Such is the nature of a live CD session.

So, is there some way to make the nvidia restricted driver work without requiring a reboot?

-Mark

---

### Post by the yawner on 2007-09-14
I may be wrong, but as far as I know the only way you can test restricted drivers on a live CD is if the driver is already included on the CD itself. I've had some live CDs that has this feature, but not Ubuntu.

---

### Post by mjpatey on 2007-09-14
Yeah, I think this is going to have to be a leap of faith.

It's funny, another interesting issue with this is that when I went to enable the restricted driver, it couldn't find it in the repos.  I guess it's already been replaced since the live CD was compiled, and there's no way to download updates in live CD sessions, so I had to find the old version in an archive on the web.  I was able to install it just fine, but of course, the reboot ruined all that.  :-)

---

### Post by mikewhatever on 2007-09-14
Sabayon has the nvidia driver on the DVD if you do not mind downloading several GBs.
[http://www.sabayonlinux.org/mod/mirrors/](http://www.sabayonlinux.org/mod/mirrors/)
I also hope you realize that a version of the driver is available in Feisty.

---

### Post by the yawner on 2007-09-14
The restricted driver is there in the repo. But I'm not sure if the sources is enabled on a live CD. You'll really need to be a bit gutsy now. :D

---

