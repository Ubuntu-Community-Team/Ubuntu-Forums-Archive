---
title: "How do I run the 3ddesktop?"
date: 2006-11-26
forum: General Help
---

### Post by xenoalien on 2006-11-26
How do I run the 3ddesktop? I have installed the package.

---

### Post by PriceChild on 2006-11-26
You can add a custom launcher to the panel to initate it.

the command is surprisingly:
```
3ddesktop
```

---

### Post by xenoalien on 2006-11-26
xenoalien@xenoalien-desktop:~$ 3ddesktop
bash: 3ddesktop: command not found

It doesn't seem to work. Was there something else I needed to install besides 3ddesktop?

---

### Post by ~LoKe on 2006-11-26
```
3ddesk
```

---

### Post by PriceChild on 2006-11-26
Sorry I got hte wrong one... been a while :)

---

### Post by xenoalien on 2006-11-26
I get an error...

xenoalien@xenoalien-desktop:~$ 3ddesk
Attempting to start 3ddesktop server.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Daemon started.  Run 3ddesk to activate.
3Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

I try to start manually but get the same error...
Could this be because of my video driver?
I think I might reinstall Ubuntu because ever since I tried to install Nvidia drivers from [www.nvidia.com](www.nvidia.com) I have had problems.
I have to keep changing the "nvidia" to "nv" in the xorg.conf file in order for Ubuntu to start up.

---

### Post by LLRNR on 2006-11-26
Hi, I installed the nVidida drivers according to [this](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29) and it works fine for me (although I have an old card, it's a GeForce MX 4000). Maybe there's a way to roll-back the install with their "official" driver and try what's in the guide... :-k (for Edgy there's something [here](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29), with an entry for a beta driver as well.).

LLRNR

---

