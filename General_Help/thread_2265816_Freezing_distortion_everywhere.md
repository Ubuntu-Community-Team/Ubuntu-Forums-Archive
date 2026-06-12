---
title: "Freezing distortion everywhere"
date: 2015-02-18
forum: General Help
---

### Post by john_hamilton2 on 2015-02-18
Hey guys could really use a hand here. I have in the past and now currently tried to get Ubuntu to work on my windows 7 system with no luck. I recently removed the windows partition and this is the only OS installed 14.04. I really would love to get this up and going. Every time I start up Ubuntu this happens.

4GB RAM, AMD Sempron processsor.

---

### Post by john_hamilton2 on 2015-02-18
Thanks for the help guys

---

### Post by grahammechanical on 2015-02-18
That is OK. Any time.

Remember, this is a user forum and it is ordinary users who try to help based on their own experiences. And we live in different parts of the world. So, it is not unusual for more than 24 hours to past before someone makes a suggestion. This is my suggestion

At the Grub boot menu select Advanced options for Ubuntu and then select Recovery mode>Resume. That will load Ubuntu using a fall back open source video driver. If that gets you to a desktop then the problem comes from using a proprietary video driver. Then use Additional Drivers to change video driver. Use the open source video driver.

What graphic adapter does that machine have? How much of its own memory does it have? Does it use shared memory (RAM)? The makers of proprietary video drivers often drop support for their video adapters that they consider obsolete. That might be what is happening here.

When we install Ubuntu and tick the box "Install third party software" we get the latest proprietary video driver installed. If we install without ticking that box we get the default open source video driver. It may be that you need to install Ubuntu without ticking the box marked "install third party software."

When you run the Ubuntu Try/live session before installing did you have the same problem?

---

### Post by john_hamilton2 on 2015-02-21
So I hit try ubuntu and I'm still having the same problems. NVIDIA GeForce 6150SE nForce 430 is my adapter.

---

### Post by dino99 on 2015-02-21
hello john,
the 6150se might be the faulty device to run a system requiring lot of power (too low specs)
install something 'light' like Lubuntu
and be sure to have made the installation with a swap partition. Please post the output of: sudo blkid

---

