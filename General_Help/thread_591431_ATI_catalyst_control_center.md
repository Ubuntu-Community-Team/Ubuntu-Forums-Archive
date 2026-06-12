---
title: "ATI catalyst control center"
date: 2007-10-25
forum: General Help
---

### Post by davbren on 2007-10-25
Hi, I'm looking to install the CCC so that I can change the vsync options coz I'm getting alot of tearing in both 3d apps and watching movies. I can't seem to do anything at the moment because direct rendering isn't enabled. I tried enabling it but that ddin't work either... any help?

---

### Post by SupWiz17 on 2007-10-25
I need some help with the very same thing. I cant even get my direct rendering on.

---

### Post by davbren on 2007-10-25
yh thats the problem, I've looked everywhere. I think its something to do wit hthe new driver. Its really annoyign me

---

### Post by davbren on 2007-10-26
Ok heres the thing, I installed the new driver and direct rendering is on WOO! but now I can't get compiz BOO!

Help! somebody!

---

### Post by onegreenparker on 2007-10-29
According to my Applications list, I have the CCC installed, but I can go into it to change anything.

---

### Post by graben3 on 2007-12-30
I have CCC installed but when I change something on my monitors configuration, it is only working in gnome failsafe session. Then in failsafe session I cannot enable desktop effects but everything is working as supposed (dual screen is configured as one big desktop). If i try to log in the normal gnome session it starts normally then hangs for about 10 seconds then get me back to login screen

How can i make one big desktop ATI CCC configuration work with beryl/gusty gibbon/gnome ?
I have a ATI radeon 9550

Should i have composite enabled???

Sould I DRI to 0666 in xorg.conf?

Server flags Xinerama = true ???

Please tell me what to do...
thank you very much

---

### Post by perixx on 2008-01-01
@graben3,

I'm suffering the same problems like others here and I don't know much about advanced video options of Xorg.

DRI is the direct rendering switch, I believe - have no idea what altering the value will do (but probably nothing good) -
it's turned on in its current state afaik.

COMPOSITE is the option to enable translucent windows, sorta like Vista's 'AERO' desktop... it will likely decrease your 2D-graphics performace a lot, though.

XINERAMA is for dual-monitor setups - but I don't know if there are any other video-accelleration functions built in.

perixx

---

