---
title: "How to properly install NVIDIA GeForce drivers on 13.04? (x64)"
date: 2013-05-04
forum: General Help
---

### Post by Cam! on 2013-05-04
[COLOR=#333333][FONT=Ubuntu Beta]I'd like to install the latest and greatest straight from NVIDIA, but I get an error message saying I need to log out of an X environment or something. Obviously using the default drivers doesn't deliver the best results.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]What exactly can I do to install the latest drivers? If it matters, I have a **2GB GeForce GTX 660 Ti.**[/FONT][/COLOR]

---

### Post by papibe on 2013-05-04
Hi Cam! 

How did you try to install the drivers?

Let's see how successful you were: could you post the results of these commands?
```
dpkg -l | grep nvidia

lsmod | grep nvidia

lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by bogan on 2013-05-05
Hi!**,Cam!**,

For full instructions to install Nvidia downloaded drivers see:[http://ubuntuforums.org/showthread.php?t=1743535&page=10](http://ubuntuforums.org/showthread.php?t=1743535&page=10) Post #1126.

One update: before installing, make sure DKMS is installed.
 Either use Synaptic Package Manager or,  from a Terminal, {Crtl+Alt+t} ```
sudo apt-get install dkms
```That will allow nvidia-installer to fix it so the driver module gets updated if the Kernal is updated, without you having to reinstall the driver.

Chao!,** bogan.**

---

