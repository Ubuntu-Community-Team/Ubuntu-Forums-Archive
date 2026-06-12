---
title: "need help in setting up a headless x11vnc server"
date: 2020-06-23
forum: General Help
---

### Post by jyanga on 2020-06-23
[SIZE=2][FONT=courier new]This is the command I use to run `x11vnc`.

```
x11vnc -xrandr -auth /var/run/lightdm/root/\:0 -xkb -geometry 1024x768 -forever -loop -noxdamage -repeat -rfbauth /etc/x11vnc.pass -rfbport 5901 -shared -create
```

The only thing I see is a terminal and a black background.

OS:  Ubuntu 18.04
Packages Installed:
[/FONT][/SIZE][COLOR=#000000][FONT=Menlo][SIZE=2][FONT=courier new]ubuntu-desktop
[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=courier new]xserver-xorg-video-dummy
[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=courier new]xvfb
[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][SIZE=2][FONT=courier new]lightdm

Help.[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by HermanAB on 2020-06-23
VNC is pretty much a Windows thing.  If you are working Linux to Linux, Linux to UNIX, then SSH is much easier.

---

### Post by jyanga on 2020-06-23
Thank you, Herman.  I understand that SSH may satisfy most needs when working with UNIX and Linux; however, there are some software that only runs on the GUI and there are situations where a machine is headless.  I am in this predicament.

Regards,
J

---

### Post by Tadaen_Sylvermane on 2020-08-02
[https://forum.kodi.tv/showthread.php?tid=354606&highlight=headless](https://forum.kodi.tv/showthread.php?tid=354606&highlight=headless)

I did a headless Kodi for a library master node. It's running on my server, this link holds the instructions. You should be able to piece it together from here.

---

### Post by HermanAB on 2020-08-02
You don't need to run X on the remote machine to use X with OpenSSH.  You just need to have the programs installed to be able to run them.  So you can install whatever you need on the remote machine, then kill Xorg. After that, you can remotely run  X programs using ssh:

$ ssh -Y user@server "gedit filename"

This is much easier and less resource hungry than running a full blown desktop that isn't really used much.

---

