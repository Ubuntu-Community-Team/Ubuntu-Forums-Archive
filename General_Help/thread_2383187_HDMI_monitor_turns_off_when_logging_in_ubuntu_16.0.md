---
title: "HDMI monitor turns off when logging in ubuntu 16.04"
date: 2018-01-22
forum: General Help
---

### Post by ndnikolov on 2018-01-22
Hi everyone,
I got DELL Precision 3520 recently and I installed Ubuntu 16.04 on it.
Everything works OK except external HDMI monitor - DELL P2417H.
When I log in, monitor goes off and cannot be awaken until disconnect and connect the HDMI cable back again or suspend/resume the laptop.
Same thing happens when screen locks after some time of inactivity. For the problem with lock I use xset -dpms to prevent monitor switching off. But I cannot make HDMI monitor not going off after log in.
Another thing is that I put this xset -dpms in ~/.xinitrc and in ~/.xsession and in both cases it does not work. I have to execute this command manually in a console in order the setting to take effect.
I used the open source x driver for intel first which is the default after installation and now I am using the nvidia driver - both have the same problem. And lets say this problem is annoying.

lspci
00:02.0 VGA compatible controller: Intel Corporation Device 591b (rev 04)
01:00.0 3D controller: NVIDIA Corporation Device 13b4 (rev ff)

I am using the intel controller.

uname -a
Linux laptop10 4.13.0-26-generic #29~16.04.2-Ubuntu SMP Tue Jan 9 22:00:44 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

If someone can help me and needs additional information, please let me know.
Thanks.

---

### Post by roshy10 on 2018-01-24
I've also found this problem with my dell XPS-15-9550 with Ubuntu 16.04 and gnome, the grey background is visible before I login, but once the screen flashes off the HDMI display never comes back on until I unplug and replug it.

---

### Post by zhart on 2018-08-23
The same problem here. Ubuntu 16.04 amd64 with last updates and Samsung S27F358FWI (from sf358 series), HDMI connection.

---

### Post by QIII on 2018-08-23
Good night, sweet thread.

zhart -- please start a new thread and describe your question in detail.

Closed.

---

