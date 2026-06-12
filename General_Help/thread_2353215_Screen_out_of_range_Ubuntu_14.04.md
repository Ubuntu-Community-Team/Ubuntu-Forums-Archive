---
title: "Screen out of range Ubuntu 14.04"
date: 2017-02-20
forum: General Help
---

### Post by andrei44games on 2017-02-20
I bought this new gaming PC that has Ubuntu installed on it.Everything is fine until I boot from the grub.I choose Ubuntu and my monitor shows this error:"Out of Range"
My monitor's resolution is 1920 x 1080.

---

### Post by wildmanne39 on 2017-02-20
How to fix your out of range problem at boot
If it is only happening in grub and you can boot into Ubuntu then please do this:
Code:
```
gksudo gedit /etc/default/grub
```
and change this line:

> #GRUB_GFXMODE=1920x1080

to this:

> GRUB_GFXMODE=640x480

Then save and exit the document.

In case you do not know it if you wait a little bit ubuntu should boot to the desktop so you can make the changes.

---

### Post by andrei44games on 2017-02-20
No,The grub looks fine and I can see everything,But after I choose ubuntu,The monitor refuses to show,It gives me a black screen and says "out of range".The grub is very visible.Ubuntu...Not so much.It shows me how it's loading,After it stops loading, the monitor says "out of range".

---

### Post by wildmanne39 on 2017-02-20
If you give it time and do not touch it the desktop should load, give it about three minutes and see please. I could see the grub when I had that issue but like you said as soon as it started to load my screen went black until it booted to the desktop.

---

### Post by andrei44games on 2017-02-20
Also,I forgot to ask,Is it any problem if my Video Card driver isn't compatible with Ubuntu?(It's not even installed)

---

### Post by wildmanne39 on 2017-02-20
Yes that is a problem, what video card do you have?

---

### Post by andrei44games on 2017-02-20
MSI GTX 1070 Aero.
The PC came installed with Ubuntu

---

### Post by wildmanne39 on 2017-02-20
You can set a nomodeset parameter in the grub menu when it boots up, but I am all most positive the out of range issue can be solved like I said in my first post and you probably have two issues the second one being that you do not have the video card driver installed.
[https://ubuntuforums.org/showthread.php?t=1613132](https://ubuntuforums.org/showthread.php?t=1613132)

If you have been holding down the power button when you see the out of range issue then you may have damaged your hard drive and corrupted files. You should still let the computer boot and give it at least 3 minutes to see if it will go to the desktop.

You can also go into the grub and chose to boot in low graphics mode.

Has ubuntu ever booted all the way?

---

### Post by andrei44games on 2017-02-20
Well,I'm not sure if it booted all the way,The background went from purple(While loading) to black,And then the error showed up,Also,I cannot turn off my computer while it's having that error.I also have to add that nor my Motherboard driver is installed,The PC is brand new,No drivers installed.
I never did hold down my power button longer than 1 second for my PC to turn off.

---

### Post by wildmanne39 on 2017-02-20
Most drivers are installed when you install ubuntu with few exceptions like the nividia driver but you should be able to boot before you install the driver using the method in my previous posts.

---

### Post by andrei44games on 2017-02-20
Ok,Thank you very much.

---

