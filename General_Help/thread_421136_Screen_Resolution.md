---
title: "Screen Resolution"
date: 2007-04-24
forum: General Help
---

### Post by Morg on 2007-04-24
Hi, I have recently changed from Windows XP to Ubuntu. When i was on XP my standard resolution was 1280x1024, as i have a 19" TFT, this is the advised resolution. However since switching over the only options i have in the screen resolution menu (System>Preferences>Screen Resolution) are 1024x768 / 800x600 / 832x624.  I am also using an ATI Radeon X800XT. Could anybody tell me if i am able to change my resolution to 1280x1024, as it just looks odd with the current ones. 
Also there is only one options to select in the refresh rate, that being 60 Hz. When my monitor can go up to 85Hz.

Thank you, 
Morg.

---

### Post by dcstar on 2007-04-24
> **Morg said:**
> Hi, I have recently changed from Windows XP to Ubuntu. When i was on XP my standard resolution was 1280x1024, as i have a 19" TFT, this is the advised resolution. However since switching over the only options i have in the screen resolution menu (System>Preferences>Screen Resolution) are 1024x768 / 800x600 / 832x624.  I am also using an ATI Radeon X800XT. Could anybody tell me if i am able to change my resolution to 1280x1024, as it just looks odd with the current ones. 
Also there is only one options to select in the refresh rate, that being 60 Hz. When my monitor can go up to 85Hz.

Thank you, 
Morg.

There are a squillion posts in the forum on how to fix issues like this, just do a forum search for them.

---

### Post by Happy_Man on 2007-04-24
Run ```
dpkg-reconfigure xserver-xorg
``` and when you get to the screen that asks for monitor resolutions, use the spacebar to select 1280x1024.

---

### Post by Morg on 2007-04-24
OK i have tried that, but it wont go past a screen talking about BUS speeds, the only option is the <ok> at the bottom. I hit enter, and nothing happens...

---

### Post by strabes on 2007-04-24
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Dave54 on 2007-04-25
> **Morg said:**
> OK i have tried that, but it wont go past a screen talking about BUS speeds, the only option is the <ok> at the bottom. I hit enter, and nothing happens...

Hit left/right to select the <ok>, then hit enter.

---

