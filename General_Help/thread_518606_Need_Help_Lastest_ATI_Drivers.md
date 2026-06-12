---
title: "Need Help Lastest ATI Drivers"
date: 2007-08-06
forum: General Help
---

### Post by Vince4Amy on 2007-08-06
Hello.

I have currently installed the ATI Radeon driver from the restricted manager. However I really need the new version of the drivers. I find the ATI Installation wiki useless as I've messed up when using it so many times.

How would I remove the driver safely from the Restricted Manager?

How do I install the latest ATI Radeon Drivers.

---

### Post by pyxu619 on 2007-08-06
Which version do you currently have?
To install the latest one, download the driver directly from ati's website. Then just follow this

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.39.4-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.39.4-inst.html) 

to install the driver. Let me say that I didn't find the newest ati driver very useful. I used the default one that ubuntu feisty came with and it works perfectly. I have an 9800xt.

---

### Post by Vince4Amy on 2007-08-06
Right i've installed that, & I ran Aticonfig, it didn't work so I changed to fglrx under driver in xorg.conf manually. I rebooted & now I get this output:

```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

---

### Post by pyxu619 on 2007-08-06
thatz what happen to me when using the newest driver too. So I went back to the default feisty version which I believe it is 8.32.4 or something around there. which you can also download from ati

---

