---
title: "No network manager applet after upgrading to 14.10"
date: 2014-11-01
forum: General Help
---

### Post by bach on 2014-11-01
After I upgraded from Ubuntu 14.04 to 14.10 I no longer see the network manager applet in the Unity bar. How can I bring it back? The computer automatically connects to my home wifi network, so networking works. The problem is that there is no network manager applet in the Unity bar. There, I only see the keyboard, bluetooth, battery, sound and clock applets. Tips are welcome.

---

### Post by Frogs Hair on 2014-11-01
Install the dconf editor if not already and navigate to org > gnome > desktop > nm-applet and see if show applet is checked.

---

### Post by bach on 2014-11-01
No, it's not. Under org -> gnome -> nm-applet: show-applet is marked. And yet I see no network manager applet in the unity bar.

---

### Post by Frogs Hair on 2014-11-01
Desktop is in the path as well but all that matters is that you found it. Try the following command and restart.  

```
sudo apt-get install --reinstall network-manager-gnome 
```

---

