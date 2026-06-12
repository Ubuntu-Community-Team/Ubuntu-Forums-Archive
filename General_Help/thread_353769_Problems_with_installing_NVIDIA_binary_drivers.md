---
title: "Problems with installing NVIDIA binary drivers"
date: 2007-02-05
forum: General Help
---

### Post by 505 on 2007-02-05
Yesterday I decided it would be nice to try out Beryl. Before I could install it, I needed to update my NVIDIA drivers. I have a Geforce4 MX 400 card. I downloaded the official binary 9631 drivers.

During installation the installer gave a warning about X.org being modular, and not being about to compile a correct kernel. The warning said X.org SDK/development files were missing. Nevertheless, the installation did continue.

After a restart, X could not start, complaining the NVIDIA kernel was 7184 but the drivers 9631. So I installed the package 'xserver-xorg-dev' and ran the driver installation again. This time the installation did not give any error messages. However, after a restart, it still couldn't start X, giving the same error message about the kernel being 7184. The strange thing is that I could run
```
sudo rmmod nvidia && modprobe nvidia && startx
```
and X would start. The NVIDIA condig utility even listed that I had the 9631 drivers.

**Question 1:** What did I do wrong during the installation of the drivers. Why wouldn't it work after a start, but did it work after removing and adding the kernel module again?

Deciding that this was not a very good situation to have, I downloaded the official 7184 drivers from NVIDIA and installed those. All went well, and X starts without a problem. However, when I start programs such as Thunderbird, Synaptic or Gedit (and possibly others) my whole systems freezes. Only the mouse is responsive. I can't even switch to another TTY. Only the reset button helps.

**Question 2:** can this be related to the driver issue, and how can I resolve this?

---

### Post by fenian on 2007-02-05
Use envy to install the latest nvidia drivers...

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

First use it to remove all the old nvidia drivers and tthen use it to install the latest nvidia drivers.

---

### Post by OffHand on 2007-02-05
[http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl+blacklist+nv](http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl+blacklist+nv)

Step 2 > Option 2

Blacklist nv

---

### Post by lewislp on 2007-02-10
I had the same problem and Step 2 > Option 2 worked for me with Feisty Fawn Herd 3 and an NVIDIA 7600.

---

