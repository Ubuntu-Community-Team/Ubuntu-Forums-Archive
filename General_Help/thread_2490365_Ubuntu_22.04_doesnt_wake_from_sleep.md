---
title: "Ubuntu 22.04 doesnt wake from sleep"
date: 2023-08-31
forum: General Help
---

### Post by julius-nepos on 2023-08-31
New xUbuntu 22.04 installation on an 8 core HP-2145 desktop server.  Not duel bool, Linux-only.  When systems goes to sleep, it wont wake up.  Uses a USB wireless keyboard but a wired USB mouse.
Maximum time before sleeping is set to be 5.5 hours.

Computer must be shutdown by powering off and rebooting, leading to open files and loss of all data to wake it up.

---

### Post by maglin2 on 2023-09-01
So I suspect your problem is that (a) (x)ubuntu doesn't wake on mouse click and (b) wifi is turned off during suspend/sleep.
I'm afraid I don't know a workaround for either, and I doubt if there is a workaround for (b) (though I believe it is possible in windows). Someone else may be able to advise wrt (a)
Edit
This may possibly be of use - I can't claim to have tried it.
[https://www.makeuseof.com/wake-your-linux-pc-from-suspend-using-usb-devices/](https://www.makeuseof.com/wake-your-linux-pc-from-suspend-using-usb-devices/)

---

### Post by MAFoElffen on 2023-09-02
I do, I do, Pick me!!!! LOL ):P):P):P

Usually, problems waking from sleep have to do with the cpu cstate setting and/or the graphics driver. You didn't post any info of what your CPU and GPU are, so answering a bit abstract to cover differing possibilities.

In /etc/default/grub, in line GRUB_CMDLINE_LINUX_DEFAULT, if you add the boot parameter "intel_idle.max_cstate=4"... Then it will limit just how far your CPU can go to sleep, so it is easier to wake up from that sleep.

---

