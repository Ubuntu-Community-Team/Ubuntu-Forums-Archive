---
title: "Help"
date: 2008-03-20
forum: General Help
---

### Post by Pheetuz on 2008-03-20
I wasnt quite sure where to put this, but heres my problem.

I installed an update for my Nvidia graphics card, restarted it all booted up as normal, but after the Ubuntu screen loaded my monitor turns itself off and dosent switch back on, so Im asuming its something wrong with the Nvidia driver that was installed by Ubuntu, wondering what I should do next to sort it so I can use my computer since Im using a computer at college to do everything at the moment.

---

### Post by kpkeerthi on 2008-03-20
From GRUB, boot into Recovery Mode. At the prompt, enter
```
dpkg-reconfigure -phigh xserver-xorg
```

And choose **nvidia** for driver and appropriate resolutions you monitor supports. Now reboot into normal mode.

EDIT: If it did not work, repeat the same step as above, instead choose **nv** or **vesa** for the driver and reboot.

---

### Post by Pheetuz on 2008-03-20
> **kpkeerthi said:**
> From GRUB, boot into Recovery Mode. At the prompt, enter
```
dpkg-reconfigure -phigh xserver-xorg
```

And choose **nvidia** for driver and appropriate resolutions you monitor supports. Now reboot into normal mode.

EDIT: If it did not work, repeat the same step as above, instead choose **nv** or **vesa** for the driver and reboot.

Thank you so much, I cant express my happiness enough.

---

