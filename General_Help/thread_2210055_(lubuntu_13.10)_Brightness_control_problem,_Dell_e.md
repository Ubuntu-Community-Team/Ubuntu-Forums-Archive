---
title: "(lubuntu 13.10) Brightness control problem, Dell e6420"
date: 2014-03-08
forum: General Help
---

### Post by hirotop on 2014-03-08
Hello, 

I am experiencing a problem in changing the brightness of the screen with my dell latitude e6420 machine with Lubuntu 13.10. 

To tell you the story, brightness control works but very buggy. When I change the brightness with the hotkey, the machine halts for 1 or 2 secs, and the brightness is changed in 2 steps instead of 1 step. And the on-screen display for the brightness control comes the last. In short, 

1. I hit the hotkey to change the brightness (1 time)

2. 1 ~ 2secs

3. Brightness changes 2 steps. 

4. Onscreen display shows. 

It was buggy even with lubuntu 13.04 but it becomes worse than before. 

Is there anyone who are experiencing the same problem? 

Thanks.

---

### Post by pqwoerituytrueiwoq on 2014-03-08
see if [xbacklight](apt:xbacklight) does better
or this script
[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1064117/+attachment/3388158/+files/backlightx.tar.bz2](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1064117/+attachment/3388158/+files/backlightx.tar.bz2)

---

### Post by hirotop on 2014-03-08
Hi, [ 						 							]("http://ubuntuforums.org/member.php?u=865458")[**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458"), 

Thank you for your help. But, they are the same...T.T

---

### Post by pqwoerituytrueiwoq on 2014-03-09
maybe the [FONT=courier new]apci_osi="!Windows2012"[/FONT] boot parameter will do something helpful

---

