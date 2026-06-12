---
title: "Made a mistake"
date: 2007-12-14
forum: General Help
---

### Post by sethfc on 2007-12-14
Hey all.

All i need to know is what "sudo ......" command do I write to change my video driver?

Basically, Through the interface on ubuntu, i changed my video driver to an nvidia driver.  Now the desktop never fully loads.

I want to start up in recovery mode and type in a generic video driver...


any help?

-seth

---

### Post by yabbadabbadont on 2007-12-14
```
sudo dpkg-reconfigure xserver-xorg
```
That should do it.

---

### Post by sethfc on 2007-12-14
ill try it...

so far i've tried this
```
sudo /etc/init.d/gdm stop
sudo aptitude remove nvidia-glx
sudo apt-get install nvidia-glx-legacy
```

that did not work

performing....
```
sudo dpkg-reconfigure xserver-xorg
```

worked great! thank you so much.  now i just gotta get my resolution/refresh rate all wrked out >.<

---

