---
title: "how do I create custom categories on Lubuntu main menu?"
date: 2018-02-04
forum: General Help
---

### Post by ardouronerous on 2018-02-04
I'm running Lubuntu 16.04 LTS.
How do I create custom categories on Lubuntu main menu? Thanks.

---

### Post by ajgreeny on 2018-02-05
Install and use alacarte; it works in 16.04 for me.

---

### Post by ardouronerous on 2018-02-05
I've tried Alacarte already, but it broke Lubuntu's menu, after I created my first custom directory, the menu broke, leaving only the options run and logout on the menu.

To fix the menu, I had to reset it to default using this command:

```
cp /usr/share/lxpanel/profile/Lubuntu/panels/panel ~/.config/lxpanel/Lubuntu/panels
lxpanelctl restart
```

---

### Post by cruzer001 on 2018-02-05
Looks like you will have to edit xml-format menu files in /etc/xdg/menu for Lubuntu.

[https://ubuntuforums.org/showthread.php?t=2184825](https://ubuntuforums.org/showthread.php?t=2184825)

---

### Post by ardouronerous on 2018-02-05
I installed MenuLibre and it works, I was able to create the custom categories that I wanted without messing up Lubuntu's menu like Alacarte did.

---

