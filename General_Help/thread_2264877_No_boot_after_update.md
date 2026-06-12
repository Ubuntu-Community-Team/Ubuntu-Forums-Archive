---
title: "No boot after update"
date: 2015-02-10
forum: General Help
---

### Post by pauser on 2015-02-10
My Ubuntu has stopped booting after an update, how can I access the last old kernel. It gets to my desktop and won't go any further, hangs so to speak. Thanks.

---

### Post by Bucky Ball on 2015-02-10
To access the previous kernel, hold down shift at boot. That should get you to the grub menu where you can boot into a previous kernel and troubleshoot what may have gone wrong. 

So you are getting to the desktop and then what? When you say it hangs, does that mean the mouse cursor doesn't move or you click on something and nothing happens. Which version of Ubuntu are you using?

---

### Post by pauser on 2015-02-10
Thanks for the prompt reply. I am using 14.04 from within xp windoze. It just does nothing, I have my desktop photo but no icons, no left hand panel, I have mouse but nothing happens. I tried rescue disk, no joy and now I have an extra Windows generic boot. No big deal, just have to watch start up otherwise it goes automatically to that and that's a dead end.

---

### Post by pauser on 2015-02-10
Did as you suggested, it got to a point where it displayed briefly two lines of numbers with, I think at the end of each line "unable to ..." it was too quick for me to focus on and read, then it booted into Ubuntu loading screen then the desktop with log in and the usual icons at top right. If I log in they disappear and then nothing happens, just my pretty picture. I'm thinking it may be quicker to do a re-instal. Nothing that needs saving other than the web page addresses I was looking at before the update. I save everything to an external hard drive as I've only allocated 16gb I think to Ubuntu.

---

### Post by Bucky Ball on 2015-02-11
You are using Ubuntu inside Windows, not installed to its own partition? That is a Wubi install, and unfortunately, even though still available, Wubi is no longer supported here or by Canonical. I suggest you create a dual-boot and install Ubuntu on its own partition. Let us know if you need help with that.

Please see [here]("http://ubuntuforums.org/showthread.php?t=2229766"). Good luck. ;)

---

