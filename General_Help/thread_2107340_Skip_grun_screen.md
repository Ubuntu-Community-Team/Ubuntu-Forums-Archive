---
title: "Skip grun screen"
date: 2013-01-21
forum: General Help
---

### Post by Blasphemous on 2013-01-21
I need to find a way to **completely skip the grub screen** and **boot directly to Ubuntu.**

I don't want to press enter every time or wait 30 seconds and I rarely boot into Windows, so there's no reason to have the grub screen displayed.
I'd like to get things to go as similar as possibile to a Linux only installation: no kernel select, no purple grub menu, no Windows entry. Just boot up the PC and wait for Ubuntu to load. 
Don't ge me wrong: I do want to keep Windows Installed. I'll boot into it when I need it, but most of the time I don't, so there's no need of grub screen.

I'm using Ubuntu 12.04 64 bit :)

---

### Post by Impavidus on 2013-01-21
Edit /etc/default/grub:```
sudo nano /etc/default/grub
```Then set GRUB_TIMEOUT to whatever value (in seconds) you like more. 0 is acceptable. Use```
info -f grub -n 'Simple configuration'
``` for a manual page. Afterwards run```
sudo update-grub
```For comparison, these are the uncommented lines of my /etc/default/grub, which is the default for non-dual booting systems. Using these settings the menu won't display.```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
To be able to boot windows easely, I suggest you set a timeout of about 3 seconds. Waiting 3 seconds during boot shouldn't be much of a problem.

---

### Post by Blasphemous on 2013-01-22
That did the trick. Thanks Impavidus ;)

---

### Post by Bucky Ball on 2013-01-22
If you ever need to get to the grub screen (to use the recovery kernel, say) then hit shift after the BIOS screen.

---

### Post by mJayk on 2013-01-22
I've  been looking at how to do this for some time on the side.  Thanks

---

