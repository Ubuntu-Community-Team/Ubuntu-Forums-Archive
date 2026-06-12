---
title: "Getting Nvidia drivers to work with GeForce MX 4000 (Solved)"
date: 2006-10-14
forum: General Help
---

### Post by PARO on 2006-10-14
I've been trying for a while now to get the nvidia-glx drivers to work. When I type in "sudo nvidia-glx-config enable" it goes through the process and makes a backup of xorg.conf, then when I close the X server it doesn't start back up, I just get a frozen black screen without the capability to write anything. So I do a hard-reboot, and then restore the backup and then I can get in again. I've tried manually changing the xorg.conf file without the use of the nvidia-glx-config, and even if I make only one change, changing "nv" to "nvidia" in the driver line, then I get the black screen after I close X. Also, 3d rendering is no longer working. Anyone know what's likely to cause this problem?

---

### Post by K.Mandla on 2006-10-14
I have one of these, and I think I used the nvidia-glx-legacy drivers, not the nvidia-glx drivers (it's been a while since I installed it). Which did you use?

---

### Post by PARO on 2006-10-15
Oh... I just checked the list for use with the legacy ones, and it's on there. For some reason I thought that they were for 2000 and below... I don't know why. Thanks!

---

### Post by K.Mandla on 2006-10-15
Great! I'll mark this as "solved."

---

