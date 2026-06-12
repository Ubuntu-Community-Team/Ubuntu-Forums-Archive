---
title: "How to make the PowerButton to do ShutDown"
date: 2012-10-18
forum: General Help
---

### Post by ThethundarBird on 2012-10-18
How to make the PowerButton to do ShutDown
 when i press the power button , i want ubuntu 12.4 to shutdown , i have installed it on external HD USB in case it matters

---

### Post by zeroseven0183 on 2012-10-18
You may need to install dconf Editor to do that.

1. Just issue this command from the Terminal:

```
 sudo apt-get install dconf-tools
```

2. Once installed, look for dconf Editor in the Unity Dash by typing **dconf Editor** then
3. Scroll to *org* > *gnome* > *settings-daemon* > *plugins* > *power*
4. On the right pane, select the desired action, that is *shutdown*, for **button-power**

Hope that helps!

---

