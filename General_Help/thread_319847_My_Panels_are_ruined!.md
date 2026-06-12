---
title: "My Panels are ruined!"
date: 2006-12-16
forum: General Help
---

### Post by jincast90 on 2006-12-16
Hello.. I tried fiddling around with my panels today, trying to add new stuff to them, taking them away and stuff like that. Then suddenly I got a nasty bug. Nothing responded so I did a reboot. After the reboot my panels looks like in this picture, and are not responsive. The rest of my Operation System works just fine but the panels are totally f*****. (Sorry the language). Anyone have an idea of what to do?

---

### Post by xopher on 2006-12-16
Try restarting the gnome-panel, to see if it fixes it.

```
killall gnome-panel
```

---

### Post by Ramses de Norre on 2006-12-16
And otherwise you could try to log out of gnome, remove the panels config directory and log back in, all panel settings will be reset then:
 ```
rm -rf ~/.gconf/apps/gnome-settings/gnome-panel
```

---

### Post by jincast90 on 2006-12-16
> **Ramses de Norre said:**
> And otherwise you could try to log out of gnome, remove the panels config directory and log back in, all panel settings will be reset then:
 ```
rm -rf ~/.gconf/apps/gnome-settings/gnome-panel
```

Where is "~" located? It isint root is it?

---

### Post by taurus on 2006-12-16
The ~ means your $HOME directory!!!  If your login name is john, then ~ is the same as /home/john...

---

### Post by jincast90 on 2006-12-16
Non of the above helped.. Any other ideas of what to do. Do I have to formate?

---

### Post by fragos on 2006-12-16
Does not responsive include right clicking an empty area?

---

### Post by jincast90 on 2006-12-16
> **fragos said:**
> Does not responsive include right clicking an empty area?

Thanks for trying to help, but I formated. It sux but I just could not get it to work. Thanks for trying anyways guys.

---

