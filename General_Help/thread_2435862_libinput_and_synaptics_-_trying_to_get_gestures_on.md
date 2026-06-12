---
title: "libinput and synaptics - trying to get gestures on trackpad to work"
date: 2020-01-27
forum: General Help
---

### Post by crackers_altitude on 2020-01-27
I have encountered the libinput and synaptics packages while in the process of getting multitouch gestures working with an Apple Magic Trackpad 2. Because there are some old webpages out there, it is not clear if the current Ubuntu* I am using should have one or the other. Apt is installing both, apparently. However, one clue that synaptics is a problem is this error :

```
synclient
Couldn't find synaptics properties. No synaptics driver loaded?
```

... Xorg.0.log (the latest one, in ~/.local, as I learned) shows libinput getting loaded ok... apparently. I put 70-synaptics.conf in /usr/share/X11/xorg.conf.d/, however, it appears not to load - hence this post. in the description of libinput, it says " ..  essentially replaces the separate -evdev and -synaptics drivers."

I am wondering if evdev and synaptics should be removed (I tried this already, I think - I'll try again), if this could explain my failure to configure the multitouch gestures - or should the entire system be upgraded to Ubuntu 19.

Some additional comments : I tried evtest as well, I found some descriptions of libinput-gestures, but I'm hesitant to get into that. touchegg isn't working, though it is reading the wishlist correctly.

*details:

libinput version 1.10.4
evtest version 1.33
libinput version 
synclient version 1.9.0
xserver-xorg-input-synaptics 1.9.0-1ubuntu1
xserver-xorg-input-libinput 0.27.1-1
X server 1.19.6 (lots more detail possibly relevant)

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic
Linux system 4.15.0-74-generic #84-Ubuntu SMP Thu Dec 19 08:06:28 UTC 2019 x86_64 GNU/Linux

---

### Post by Claus7 on 2020-02-05
Hello,

searching the issue as well, I found out that synaptics does not support by default multitouch. I was able to have multitouch enabled in firefox for example, yet pressing Ctrl at the same time. Opera did not follow this pattern though. Both libinput and synaptics installed.

If you want multitouch support then I would advice you to use fusuma: [https://askubuntu.com/questions/1034624/touchpad-gestures-in-ubuntu-18-04-lts](https://askubuntu.com/questions/1034624/touchpad-gestures-in-ubuntu-18-04-lts)

Regards!

---

### Post by crackers_altitude on 2020-02-06
found this today : 

[https://git.kernel.org/pub/scm/linux/kernel/git/jikos/hid.git/commit/?h=for-next&id=9d7b18668956c411a422d04c712994c5fdb23a4b](https://git.kernel.org/pub/scm/linux/kernel/git/jikos/hid.git/commit/?h=for-next&id=9d7b18668956c411a422d04c712994c5fdb23a4b)

that means Google contributed patches to the Linux kernel in December of 2018, for kernel 4.20. Ubuntu is at 4.15.0-76-generic, as of my 18.04.4 LTS installation. perhaps the relevant signals/code isn't even in the kernel - I mean, that would have to be the case - so this must be futile if the kernel is less than 4.20.

---

### Post by Claus7 on 2020-02-11
Hello,

using ubuntu 20.04 with kernel 5.4.0 I cannot see any difference. Yet, you are having an apple system so your case might be different.

Regards!

---

### Post by crackers_altitude on 2020-10-02
quick update:

apple magic trackpad 2 works 
upgraded to 20.04.1 LTS
linux kernel 5.4.0-48-generic


two-finger scroll
tap to click

---

