---
title: "X server fails to start after installing updates!"
date: 2006-08-12
forum: General Help
---

### Post by Carrots171 on 2006-08-12
First of all: I have an Nvidia graphics card and it was working fine with the proprietary Nvidia driver from the repositories before I installed the updates! 

I came back from vacation a few days ago and opened up update-manager. It told me that I had 180 updates to install and I installed them. One of the updates was the Nvidia driver. (nvidia-glx). I rebooted after the update, and a blue screen of death popped up and said this:

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

The X server output is as follows:
> 
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug 13 08:17:51 2006
(==) Using config file: "/etc/X11/xorg.conf"
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined
symblol: _glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)
FATAL: Module nvidia not found.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found 


I've tried re-installing "nvidia-glx" and "nvidia-kernel-common", but I get the same result. How can I fix this problem? How can I get X to work again? Thanks in advance for your help.

---

### Post by Carrots171 on 2006-08-13
Never mind. I found out that linux-restricted-modules wasn't installed in the update because of a problem with the server. I installed them and everything works now.

---

### Post by mwigge on 2006-08-21
what modules?


i have exactly the same problem.. please aid :)

---

### Post by jlachovsky on 2006-08-23
Yeah I also am having this problem.  Not a tremendous big deal, because I plan on reinstalling soon anyways, but I would like to know how to fix it, and what caused it.

---

### Post by jlachovsky on 2006-08-23
Figured it out.  [http://ubuntuforums.org/showthread.php?t=241350](http://ubuntuforums.org/showthread.php?t=241350)

---

