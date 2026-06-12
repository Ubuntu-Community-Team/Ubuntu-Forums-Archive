---
title: "screen rez problem"
date: 2007-02-13
forum: General Help
---

### Post by virtualsnyper on 2007-02-13
hey a;;. I wanna say thx for helping me out. I love that linux has a tight community :P. I was wondering if anyone would know why I couldn't get my screen resolution above 1024...I have a 7900gs, im running edgy x64. Nvidia drivers installed....what gives?

---

### Post by Adramelech on 2007-02-13
try
Systenm->Preferences->Screen resolution

---

### Post by Tmi on 2007-02-13
Check you /etc/X11/xorg.conf

If you scroll down a bit you'll see a listing of resolutions. I'd bet your's doesn't contain anything aboive "1024x768". Add whatever you want to use to the list and it should work if the other things are setup correctly as far as I know. Don't forget to backup xorg.conf before changing it in case it doesn't work.

---

### Post by housam on 2007-02-13
Open your xserver-xorg 
```
sudo dpkg-reconfigure xserver-xorg
```
and press enter for every thing ( leave every thing as it is ) till you get the sitting page as in the attachment and select 1280x800 ( by pressing space ) and continue to go out.

---

