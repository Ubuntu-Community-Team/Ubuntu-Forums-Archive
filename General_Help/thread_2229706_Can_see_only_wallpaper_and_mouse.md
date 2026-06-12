---
title: "Can see only wallpaper and mouse"
date: 2014-06-14
forum: General Help
---

### Post by pedro_reis on 2014-06-14
Hello, After an upgrade ubuntu automatically did, I can no longer see the top and left bars. I can't also enter terminal using ctrl+alt+T. The only thing I'm able to do is to open ctrol+alt+f2.
I can navigate only in the visitor's mode. Already tried some things like unity --reset and unity-tweak-tool but nothing worked.
Can anybody give me some help??

The video card is an AMD one.
Notebook samsung RV415

---

### Post by grahammechanical on 2014-06-14
You can try right click the desktop and select Change Desktop Background. That will open System Settings>Appearance but from there you can get to System Settings>Software and Updates>Additional Drivers tab and experiment with video drivers. You can also try

```
dconf reset -f /org/compiz/
```

and

```
setsid unity
```

Regards.

---

### Post by pedro_reis on 2014-06-15
> **grahammechanical said:**
> You can try right click the desktop and select Change Desktop Background. That will open System Settings>Appearance but from there you can get to System Settings>Software and Updates>Additional Drivers tab and experiment with video drivers. You can also try

```
dconf reset -f /org/compiz/
```

and

```
setsid unity
```

Regards.


When I type 
dconf reset -f /org/compiz/

this message appears:
error: cannot autolaunch D-Bus without X11$DISPLAY

---

### Post by grumblebum2 on 2014-06-15
If you are running from a virtual terminal, try...
```
DISPLAY=:0 dconf reset -f /org/compiz/
```

Then reboot...
```
sudo reboot
```

---

