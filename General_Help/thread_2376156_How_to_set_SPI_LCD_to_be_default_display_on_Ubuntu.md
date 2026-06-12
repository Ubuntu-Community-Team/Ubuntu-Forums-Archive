---
title: "How to set SPI LCD to be default display on Ubuntu?"
date: 2017-10-30
forum: General Help
---

### Post by rezaee on 2017-10-30
I have a 2.2" TFT-LCD and an ARM-based board(nanopi-m1) with Ubuntu-server-16.04 on it.  I have a framebuffer driver named NOTRO([https://github.com/notro/fbtft](https://github.com/notro/fbtft)) that uses fbtft support on kernel and makes my display work by this commands:

```
    sudo modprobe fbtft_device custom name=fb_ili9341 gpios=reset:1,dc:201,led:6 speed=16000000 rotate=90 bgr=1
```

With above command my LCD turns on and I have a blank black screen. Then I must run this command to have my x-manager screen:

```
    FRAMEBUFFER=/dev/fb8 startx
```

But now, I like to change my linux settings to do these commands automatic at startup. but I don't know how?

---

### Post by rezaee on 2017-10-30
I should add that, I have installed > xorg,xserver-xorg-video-fbdev, openbox too!

---

