---
title: "No GUI after Xubuntu base update, Trusty"
date: 2014-05-10
forum: General Help
---

### Post by ericmark4 on 2014-05-10
So, just when I was about to sign off on Trusty being the best OS ever....today I ran Software Updater, it found a few updates to Xubuntu base, which I installed, got the reboot required message---and when I try to reboot I get a blank screen. 

Tried logging in from the command line, then startxfce4. It says X is already running; when I try ctrl/alt/F7 I get the same blank screen. I hope I am wrong, but I suspect this might be related to the integrated Nvidia 6 series graphics on my vintage 2008 eMachines ET 1161-01. That caused all manner of problems on 12.04, to the point I went back to Lucid for awhile, and spent more time in Win 7 than I wanted to....when I installed 14.04 last month, I held my breath but the graphics worked fine. Now this.

I have the latest tested Nvidia driver---304.117---and the only tweak I made to the system was to turn off desktop compositing. Both of those on the day I installed Trusty last month; no problems since, until this morning.

Anyone else have this problem? Any ideas? Thanks.

---

### Post by slooksterpsv on 2014-05-10
I guess I'm lucky, there are a few things you can try:
0. In terminal run:
```

sudo killall xfwm4
sudo Xorg -configure
sudo cp ./xorg.conf.new /etc/X11/xorg.conf

```
Reboot.

1. Reboot, get to grub, add the option nomodeset to the end of the boot option
2. Uninstall the nvidia 304.117 driver
3. If #2 works, try installing a different driver

---

### Post by ericmark4 on 2014-05-11
> **slooksterpsv said:**
> I guess I'm lucky, there are a few things you can try:
0. In terminal run:
```

sudo killall xfwm4
sudo Xorg -configure
sudo cp ./xorg.conf.new /etc/X11/xorg.conf

```
Reboot.

1. Reboot, get to grub, add the option nomodeset to the end of the boot option
2. Uninstall the nvidia 304.117 driver
3. If #2 works, try installing a different driver

Thanks, but I just reinstalled Trusty from scratch. So far all is well. Thanks for the ideas. Will keep them in mind if this happens again. Nvidia integrated graphics and (X) Ubuntu just don't mix well, I've learned the hard way. I still like Xubuntu so much I will put up with it, for now. If it happens again, I'm gonna try Mint MATE.

Cheers....

---

