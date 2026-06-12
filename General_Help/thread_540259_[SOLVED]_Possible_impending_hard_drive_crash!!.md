---
title: "[SOLVED] Possible impending hard drive crash!!"
date: 2007-09-01
forum: General Help
---

### Post by dpar on 2007-09-01
Heres the setup:
HD0(which is called hdc) Is the drive with MBR and Windows XP
HD1(which is called hdd) Has Ubuntu and Kubuntu on it on seperate partitions

I have been getting a few indications that hdc is going to crash.
No biggy, because I haven't used Windows in a year.

Can I remove hdc (if it crashes) and put hdd in the master boot plug and still have my Linux?
I imagine I would have to reinstall grub to hdd (since it was on the MBR of hdc before), if so, how would I go about doing this?

Thanks for any help.

---

### Post by tgalati4 on 2007-09-01
sudo grub-install /dev/hdc1

(That's after you have moved the drives.)

Check /boot/grub/device.map to see what your devices are called.

---

### Post by dpar on 2007-09-01
Thank you! I figured it would be something simple like that, but I wanted to confirm before everything went south.

---

