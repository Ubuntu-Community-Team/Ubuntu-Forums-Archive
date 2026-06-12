---
title: "screen resolution"
date: 2004-11-15
forum: General Help
---

### Post by wilhelm on 2004-11-15
just a quick Question, onthe fisrt machine wher eis installed ubuntu, i can change me resolution to 1024*768 and it is using 82810 GMCH card, sum onboard thing.

where at home i installed it this w/e, i can only change to 800*600, and i'v got a nvidia tnt2 32 mb card ?? is it perhaps the drivers for nviidia that is incorrect ? or not upto date ?

---

### Post by tidalwav1 on 2004-11-15
Just out of curiosity, did you leave your monitor on throughout the entire Ubuntu installation? Ubuntu seems to try to probe the monitor for the best video settings in addition to the video card. If the monitor was off during some of the installation chances are the optimal settings aren't in there and making a new X Config file or just reinstalling Ubuntu will most likely fix the problem.

---

### Post by ynef on 2004-11-15
The piece of hardware that is limiting what resolution you can use is the monitor. Find your monitor's specs in either the manual or online, especially the lines about horizontal and vertical refresh rate.

To make sure that your monitor does not blow up, if the autodetection can't detect what monitor you've got it uses very sensible defaults. These defaults prevent you from using all the higher resolutions that your monitor can support.

---

### Post by wilhelm on 2004-11-15
[QUOTE=ynef]The piece of hardware that is limiting what resolution you can use is the monitor. Find your monitor's specs in either the manual or online, especially the lines about horizontal and vertical refresh rate.

To make sure that your monitor does not blow up, if the autodetection can't detect what monitor you've got it uses very sensible defaults. These defaults prevent you from using all the higher resolutions that your monitor can support.[/QUOTE]
 thanks, i'll try config the monitor again, i think it mighta went off while the installation was busy, can't recall. but i will give it another go...

---

### Post by spirospr on 2004-11-15
Try reconfiguring  xfree86. I had some problems with my resolution but after some experiment with xfree configuration i managed to achieve a desired resolution.

sudo dpkg-reconfigure xserver-xfree86

Pass all in default settings and experiment in diferent settings for display choices.

Installing nvidia drivers might give some help

check this post

[http://www.ubuntuforums.org/showthread.php?t=3692&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=3692&highlight=nvidia)

Hope i offered some help...... :wink:

---

