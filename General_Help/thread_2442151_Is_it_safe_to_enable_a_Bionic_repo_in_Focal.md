---
title: "Is it safe to enable a Bionic repo in Focal?"
date: 2020-04-30
forum: General Help
---

### Post by mfox on 2020-04-30
My problem, in a nutshell, is that the 5.4 LTS kernel doesn't work properly with my iMac computer; it takes over 3 minutes to boot, about 2 minutes to wake when the display goes to sleep, and about 2 minutes to shut down. (I have filed a bug report on this.) However, the 4.15 LTS kernel, which was retained from my upgrade from Bionic, works well. What I would like to do is be notified of 4.15 kernel updates so that I can keep it up to date with security fixes. Since 4.15 isn't in the Focal repositories, it won't do that. My thinking is that if I add the correct Bionic repo to my sources (Bionic Security?), I would get these kernel updates, but I'm concerned that doing so could cause problems with other software that shouldn't be installed or upgraded from the Bionic repo. Is there a reason to be concerned about this, or would it be a good thing to add the appropriate Bionic repo to my Focal sources?

---

### Post by dino99 on 2020-04-30
First you might identify the warnings/errors logged via 'journalctl -b' against the focal kernel ( i suppose some chipset/hardware are not well identified; which is quite strange due 4.15 been well supported)

But its easier and safer to simply download  the desired kernel from  [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux) into a dedicated subfolder,

then, cd to that subfolder and via 'sudo dpkg -i *' install it
Voila

---

### Post by mfox on 2020-05-01
> **dino99 said:**
> 
 ....
But its easier and safer to simply download  the desired kernel from  [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux) into a dedicated subfolder,

then, cd to that subfolder and via 'sudo dpkg -i *' install it
Voila
That's what I have been doing so far, and it is easy. I was concerned about not getting notice of security updates, although when one is issued, I seem to find out about it quickly enough from OMG!Ubuntu or other Linux sites.

---

### Post by mc4man on 2020-05-01
> **mfox said:**
> That's what I have been doing so far, and it is easy. I was concerned about not getting notice of security updates, when when one is issued, I seem to find out about it quickly enough from OMG!Ubuntu or other Linux sites.

The kernel package  updates  are usually to the kernel metapackages, not to the kernel packages themselves. So adding bionic main repo won't help as the meta package names are the always/all the same.
 See screen for example in 20.04., those are the same names for all Ubuntu releases.
The only variation to those meta names are the HWE ones, but that's always forward, not back..

(- technically 16.04's HWE would be 18.04's release kernel so that's what you'd use but not advised..

---

### Post by mörgæs on 2020-05-02
> **mfox said:**
> it takes over 3 minutes to boot, about 2 minutes to wake when the display goes to sleep, and about 2 minutes to shut down.

Do you see the same in a live boot of 20.04?

---

### Post by mfox on 2020-05-02
Yes, mörgæs, I do see the slow boot in a live boot of 20.04. I can see why you ask this, though. There could be something on my upgraded system that is causing the problem.

---

### Post by mfox on 2020-05-02
> **mc4man said:**
> The kernel package  updates  are usually to the kernel metapackages, not to the kernel packages themselves. So adding bionic main repo won't help as the meta package names are the always/all the same.
 See screen for example in 20.04., those are the same names for all Ubuntu releases.
....

Right, but I had been thinking that if I had the 18.04 repo enabled, I would see the same as your screenshot, but for the 4.15 kernel since it is what I have on my system and it would be in that repo.

---

