---
title: "Graphics problems on Gutsy &amp; Hardy"
date: 2008-04-26
forum: General Help
---

### Post by grahams on 2008-04-26
Looking for a workaround/fix for Compaq n610c on Gutsy / Hardy
I'm using a Compaq N610c laptop on feisty without major issue. However on either Fiesty or Hardy the resolution is locked to the native 1400x1050 and can not be changed to lower resolution.

I submitted this as a bug several months ago and others have seen the same issue.
[https://bugs.launchpad.net/ubuntu/+s...ti/+bug/160871](https://bugs.launchpad.net/ubuntu/+s...ti/+bug/160871)

I'm hoping someone knows how to workaround this with the new releases of Ubuntu.

Thanks in advance.

---

### Post by Rocket2DMn on 2008-04-26
grahams, I am responding to the launchpad bug report.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/160871](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/160871)

---

### Post by grahams on 2008-05-07
Solved

add the following to xorg.conf in the device section

Option "NoDDC"

---

