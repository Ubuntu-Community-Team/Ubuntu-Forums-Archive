---
title: "vmware causes system to come to grinding halt"
date: 2007-08-19
forum: General Help
---

### Post by eqo314 on 2007-08-19
HI,

I installed vmware on feisty to test it.  I created a virtual machine and ran the xubuntu live cd from it.  Seems to run fine until I load firefox.  Firefox causes the host machine to come to a grinding halt.  The desktop turns black and white, looks like the machine run as 1 frame per minute.  I can't do a alt+F2 xkill to kill vmware.  After about a 5 minute wait, the machine runs fine again and vmware is no longer running.  Has anyone else seen this problem?

I'm runnning:
AMD 64 3800+ X2
 ASUS M2NPV-VM Socket AM2 
1GB DD2 Ram
onboard vid, onboard sound.
Ubuntu 7.04

Has anyone else seen a problem like this with vmware?

---

### Post by fjgaude on 2007-08-20
I've not had any problems at all. My hardware is not unlike yours, except for the video board, a GeForce 7600 GS.

How much memory did you allocate to the guest?

frank

---

### Post by eqo314 on 2007-08-20
512mb.   should i put more?

on a more ancient machine, 2.4ghz pentium 4, 1gb ddr ram, i was able to load windows xp and xubunut (not concurrently) as guest os's.  with no issue

---

### Post by fjgaude on 2007-08-21
That's what I use, 512 megs. It's likely the video built-into the motherboard... can't say for sure.

You've installed the tools, eh?

frank

---

