---
title: "Chrome flickers on Ubuntu 16.04"
date: 2016-09-03
forum: General Help
---

### Post by sonicking on 2016-09-03
Hi,

I have Ubuntu 16.04 and I use Chrome to browse the internet  But I notice that the screen would flicker sometimes.  This seems to be a common problem and a potential fix is said to be found here: [https://bugs.chromium.org/p/chromium/issues/detail?id=606152#c73](https://bugs.chromium.org/p/chromium/issues/detail?id=606152#c73)

But this fix is purge command.  


```
sudo apt-get purge xserver-xorg-video-intel
```


I am afraid to try it because if this goes wrong, I may lose a driver.  Can someone give your thought on this issue?  Is it "safe" to run this command and can undo it if needed?

---

### Post by grege2 on 2016-09-04
It depends on your video chipset. It is safe on modern systems with integrated Intel video. No problems on mine with a Haswell i5 

If it fails then boot to a command line and

```
sudo apt-get install xserver-xorg-video-intel
sudo reboot 

```
Then you are back where you were

---

