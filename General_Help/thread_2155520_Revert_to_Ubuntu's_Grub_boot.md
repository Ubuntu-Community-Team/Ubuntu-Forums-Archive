---
title: "Revert to Ubuntu's Grub boot"
date: 2013-06-18
forum: General Help
---

### Post by tgross35 on 2013-06-18
Hello all,

I have stepped out of my Ubuntu shell and have been messing around with other Linux distros. However, whenever I install a new distro, it installs its own version of GRUB; I would like to stick with Ubuntu's, since that is the one I use the most and, since I often have to edit GRUB, it makes sense (also the GRUB configuration utility doesn't work well with Fedora or Fedora's bootloader.) Does anyone have any idea how I can set Ubuntu's grub to work by default? By the way, GRUB2 of course. Thanks,

T

---

### Post by grahammechanical on 2013-06-18
Can you boot into Ubuntu? If so run

```
sudo update-grub
```

and see if it detects the other operating systems. Then run

```
sudo grub-install /dev/sda
```

That is assuming that you only have one hard disk and Ubuntu is installed on sda. That will put Ubuntu back in control of Grub in the MBR.

Regards.

---

### Post by tgross35 on 2013-06-18
Thank you kindly, just what I was looking for.

---

