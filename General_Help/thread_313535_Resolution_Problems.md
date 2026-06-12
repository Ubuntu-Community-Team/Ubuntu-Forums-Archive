---
title: "Resolution Problems"
date: 2006-12-06
forum: General Help
---

### Post by Roman78 on 2006-12-06
Hello there.

I'm new here. I just downloaded Ubuntu 2 weeks ago. Now i installed it on a P-IV 2.8 and on a Core 2 Duo 6300.

On the Core 2 Duo i have a 20" TFT screen whit a native resolution from 1600x1200. But when i use that resolution i get a 1280x1024 resolution whit a spanning 1600x1280. (on Windows i use 1600x1200).

Than the next problem: On the P-IV 2.8 i have a TNT2 whit 32 mem. I Installed Ubuntu on a 19" TFT whit an native resolution of 1280x1024. Now i connected it to a 17" Dell TFT screen also whit a native resolution of 1280x1024, but i can only use 640x480 and 800x600. Why is that???

---

### Post by princemackenzie on 2006-12-06
The quick and dirty answer is these monitors are different and are confusing the configuration of your X-windows configuration.

When you use a new monitor, use this code in a terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

That will reconfigure your X GUI for the monitor you are using.

---

### Post by strabes on 2006-12-06
you should also add the resolutions you want to the Screen section of your /etc/X11/xorg.conf

Ubuntu will detect the native resolution of the screen (I think) and display the correct resolution.

---

### Post by bradleyd on 2006-12-06
what driver are you using for your vid card?

---

### Post by Roman78 on 2006-12-06
Strange... On that 17" screen i cant get other resolutions than 640x480 and 800x600. Now i reconnect the 19" screen and i can choose more (bigger resolution).

On that configuration utility i entered some resolution (up to 1600x1200) and i can choose all those resolutions.

I still have the default driver from Ubuntu. Should i use Nvidia drivers?

---

### Post by bradleyd on 2006-12-06
what does your xorg.conf under monitor section say. I would try nvidia driver. Also what does xorg.conf say under section screen?

---

### Post by strabes on 2006-12-06
you should always update your video cards. Go [here](https://help.ubuntu.com/community/Video) for instructions to do so.

---

### Post by Roman78 on 2006-12-11
I tried to upgrade my drivers but it wont work.

I have a TNT2 M64 card whir 32 Meg.

So i tried the legacy driver but i'm unable to download it. When i use the Nvidia-glx driver ubuntu wont boot anymore. 

When i try to download the legacy driver whit the "Add/Remove Application" utility i get this message:

```

NVidia binary X.Org 'legacy' driver cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.

```

And when i try it via the console (sudo apt-get install nvidia-glx-legacy nvidia-xconfig nvidia-settings) i get this message:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-legacy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-legacy has no installation candidate

```

---

### Post by Scotian on 2007-03-13
Yeah, I have the same problem.... I have a Nvidia TNT2 M64 32meg onboard Video, on my P3 Compaq Presario.

I'm a complete noob to linux.  I refurbish older computers and give them away to low income families.  Most systems only have a 32meg video.

---

### Post by medya on 2007-04-25
hey guys here is[ the solution ]("http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html")

---

