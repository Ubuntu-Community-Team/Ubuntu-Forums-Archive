---
title: "Cairo-Dock Causes Line on Screen"
date: 2016-08-05
forum: General Help
---

### Post by texpat on 2016-08-05
I finally made the jump to Xenial today and found that Cairo Dock causes a grey band to appear on the lower part of the screen. This didn't happen on trusty. Any ideas on how to get rid of this?

[ATTACH=CONFIG]270588[/ATTACH]

Thanks for reading Tx

---

### Post by QDR06VV9 on 2016-08-05
What is the output of this...paste it back here.
```
inxi -SG
```
And are you running a Compositor like compiz or compton?

---

### Post by texpat on 2016-08-05
```

System:    Host: homedtp Kernel: 4.4.0-31-generic x86_64 (64 bit) Desktop: Xfce 4.12.3 Distro: Ubuntu 16.04 xenial
Graphics:  Card: NVIDIA GF104 [GeForce GTX 460 SE]
           Display Server: X.Org 1.18.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz, 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on NVC4 GLX Version: 3.0 Mesa 11.2.0

```

As to compositors: I don't really know. I haven't added one to the standard stuff that comes with the distro, so I guess that makes it "no"?

---

### Post by vasa1 on 2016-08-05
It's easy to check if you have something installed:
```
07:00 AM ~ $ dpkg --get-selections | grep -iE '(compton|chrome)'
compton						install
google-chrome-stable				install
xserver-xorg-video-openchrome			install
07:00 AM ~ $ dpkg --get-selections | grep -iE '(compton|compiz)'
compton						install
07:00 AM ~ $ 

```In my example, I have compton but don't have compiz. The follow-up would be to check if something installed is actually running. You can check that with *pgrep* or *top*.

If you're on a relatively vanilla Xubuntu, compton and compiz are not installed by default. Neither is Cairo Dock for that matter.

The answer maybe in this link: [Horizontal Line Across Screen on Xfce]("https://nochkawtf.wordpress.com/2015/05/03/horizontal-line-across-screen-on-xfce/").

---

### Post by texpat on 2016-08-06
Hi vasa1,

that link had the answer. Thanks a ton!

---

### Post by vasa1 on 2016-08-06
> **texpat said:**
> Hi vasa1,

that link had the answer. Thanks a ton!Good to know! Maybe you can drop in there and thank the author :)

---

