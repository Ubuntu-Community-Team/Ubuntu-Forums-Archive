---
title: "FGLRX Triple Screen - Can't Get Past Login If Xinerama Enabled"
date: 2014-06-07
forum: General Help
---

### Post by togmolodon66 on 2014-06-07
Hi,

I'm currently evaluating Trusty, I have a triple screen desktop (Radeon 5450) using the default open source video driver. Although it works, unfortunately there are some annoying quirks, namely:
[LIST=1]
[*]Blinking cursor (confirmed as bug in launchpad [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1278223](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1278223))
[*]Cursor becomes horrible when accessing applications running via Citrix XenApp, and Wine, aside from the blinking cursor mentioned earlier, the pointer also shows the background UI instead of the actual application (it's hard to describe, I wish I could show and sample video).
[/LIST]

Now onto the real issue, tried replacing the video driver using both stable AMD 14.4 and beta 14.6, to no avail. I can't get the third screen to work. Changes to xorg.conf gets overwritten at boot so I had to resort to tweaking /etc/init/gpu-manager.conf and commented the first four lines so that changes to xorg.conf will be retained. I can enable the 3rd screen using amdcccle but the third screen stays black despite repeated reboot, only the X cursor is visible. Also enabled Xinerama, and after reboot I was presented with three active screens, BUT, when I entered my username and password, the desktop does not load, even after waiting an hour. 

Thanks for the help.

---

