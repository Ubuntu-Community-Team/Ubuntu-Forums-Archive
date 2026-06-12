---
title: "3ddek"
date: 2007-02-18
forum: General Help
---

### Post by Orfeus on 2007-02-18
i got problem with 3desktop

```
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)
```


i tried 
```
sudo dpkg-reconfigure xserver-xorg
```

but i think i m doing something wrong because it cannot run 3ddesk.

Any help?

---

### Post by mcduck on 2007-02-18
What graphics card you have & have you installed drivers for it?

---

### Post by Orfeus on 2007-02-18
i got n videa geforce go 7600

i did the thing with

```
sudo dpkg-reconfigure xserver-xorg
```

but i probably did something wrong

anyway something messed my resolution and my colors after the configuration

---

### Post by Jucato on 2007-02-18
You need the binary/proprietary NVIDIA drivers (nvidia-glx) to get 3ddesktop to work, since it requires Direct Rendering.

---

### Post by Maestro23 on 2007-02-18
> **Orfeus said:**
> i got n videa geforce go 7600

i did the thing with

```
sudo dpkg-reconfigure xserver-xorg
```

but i probably did something wrong

anyway something messed my resolution and my colors after the configuration

Need to get the correct driver for your card from Nvidia's site.

> 1. Get and run the envy script: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

or

2. Use this HOW-TO: [http://ubuntuforums.org/showthread.php?t=336412](http://ubuntuforums.org/showthread.php?t=336412)

Good luck.

---

### Post by Orfeus on 2007-02-18
thanks that help me! it's working now but my screen resolution and colors are not ok.
How do i get back the default?

---

### Post by mcduck on 2007-02-18
you should get nVidia's own control panel when you install the official drivers. I believe it's somewhere under Applications menu, but I'm not sure as all my computers have Ati cards..

---

### Post by Orfeus on 2007-02-18
i thought i found it but now i get another error 

```
 Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd) 
```

---

