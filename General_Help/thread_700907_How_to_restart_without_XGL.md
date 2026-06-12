---
title: "How to restart without XGL"
date: 2008-02-18
forum: General Help
---

### Post by enchance on 2008-02-18
I have XGL installed for Compiz to work and I noticed that it really bogs things down because of it. I know how to turn compiz on/off but is there a way to temporarily disable XGL as well?

---

### Post by enchance on 2008-02-19
Got it. You use the two commands to turn XGL on/off

Turn off
```
gnome-xgl-switch --disable-xgl
```

Turn on
```
gnome-xgl-switch --enable-xgl
```

---

### Post by cwgannon on 2008-02-19
I'm getting a "command not found" error.  Is gnome-xgl-switch part of another package that I've not installed?

---

### Post by sub_acoustic on 2008-02-20
I really need this too.
Xgl was interfering with my ubuntu studio apps
and compiz-switch works, but only switches off compiz, not Xgl
Doesn't look like gnome-xgl-switch is available in any ubuntu packages
Could someone please add it or let us know how to install it and from where?

---

### Post by Sera88 on 2008-02-27
I second that. After I installed Compiz and XGL, I can't find a way to play ePSXe emulator with *Pete's MesaGL Driver 1.76*. *Pete's XGL Driver 2.8* or other drivers don't work on my system, as I have such an outdated graphics card (nVidia GeForce2 MX / MX400). The Compiz and the desktop effects work well though.

---

### Post by AMM6 on 2008-02-27
i installed xgl and now i cant even log in without gnome failsafe.  HOW DO I UNINSTAL IT

---

### Post by AMM6 on 2008-02-27
nvm i  have been given the code to remove it
enter in terminal:
sudo apt-get remove xserver-xgl

---

### Post by jw5801 on 2008-02-29
To disable it temporarily, (ie. without uninstalling it) create a file called ~/.config/xserver-xgl/disable, you can do this with the following command:
```
touch ~/.config/xserver-xgl/disable
```

Simply remove the file to login with Xgl again.

---

### Post by Sera88 on 2008-03-01
**jw5801**, that works! Incredible. I thought this couldn't be done, and that's why I didn't want to even install XGL, but it's OK now because it can be set off by creating that file.
Heh, the tip also shows up when one installs XGL and the notice comes up in the top right corner.

Thank you very much, jw5801. This issue is now solved.

---

