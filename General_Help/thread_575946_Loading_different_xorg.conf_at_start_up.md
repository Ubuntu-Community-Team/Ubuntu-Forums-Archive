---
title: "Loading different xorg.conf at start up"
date: 2007-10-14
forum: General Help
---

### Post by wfeltmate on 2007-10-14
Hi, I have installed a copy of Ubuntu on to a portable USB hard drive I own, as I am frequently called upon by various friends and family members to help troubleshoot or fix their computers; of which it is not uncommon for their computer to be unable to load the OS. Usually Windows.

What I was wondering, is that since I am bound to come across many different hardware configurations - specifically graphics cards - I was wondering if anyone knows of a way to choose a specific, premade xorg.conf file during startup. I have my primary one setup for my ATi card and another using the nv driver, but I was hoping for something a little more fine tuned, to make my life a little easier while fixing the problem.

Presently I boot in to recovery mode so the xserver doesn't start, use the cp command to choose the specific xorg.conf file and then exit recovery mode and start the xserver. Is there anyway to make this process a little simpler; preferably something similar to the boot options GRUB gives me.

Thanks.

---

### Post by r-mo on 2007-10-14
use a vesa driver, that 'should' work with anything.  Also gutsy has bulletproof X and displayconfig-gtk which makes it a doddle :)

---

