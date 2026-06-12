---
title: "Xorg won't start with Early KMS"
date: 2019-04-27
forum: General Help
---

### Post by vixtron on 2019-04-27
I'm using [FONT=courier new]nvidia-drm.modeset=1[/FONT] in grub's kernel params to boot with NVIDIA early KMS enabled, but it won't start the Xorg session unless I start it using [FONT=courier new]sudo startx[/FONT] for the first time from the tty and then use GDM properly.
I'm using 19.04, here is my dmesg and Xorg log [https://termbin.com/oag9](https://termbin.com/oag9)

I saw the same issue on Ask Ubuntu before but none of the solutions worked, could this possibly be the distro's fault?
EDIT: when I try to start the x session using startx, I get [FONT=courier new]xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)[/FONT]

---

### Post by dino99 on 2019-04-27
be sure to use the recommended nvidia driver  with your card, possibly not the latest version published. (and only from the ubuntu archive, not downloaded from third party)

---

### Post by vixtron on 2019-04-27
I tried installing nvidia-390 but the issue persists, this is not from the graphics-drivers ppa

---

