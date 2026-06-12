---
title: "[SOLVED] Cannot add applets to panel"
date: 2008-05-30
forum: General Help
---

### Post by adityakavoor on 2008-05-30
When I right click on any panel and try to add a launcher I get the following error message - see attachment

What is the probelem ? :(

---

### Post by cubeist on 2008-05-30
you could try
```
sudo dpkg-reconfigure gnome-panel
```
This might fix it, also have you added any applets other than what comes with ubuntu?  I used to get this message in feisty occasionally, and I found that logging out and then logging back in fixed it.

---

### Post by adityakavoor on 2008-05-30
> **cubeist said:**
> you could try
```
sudo dpkg-reconfigure gnome-panel
```
This might fix it, also have you added any applets other than what comes with ubuntu?  I used to get this message in feisty occasionally, and I found that logging out and then logging back in fixed it.

Thanks for the reply. 

It was set right after I did ```
apt-get install gnome-applets
```

---

