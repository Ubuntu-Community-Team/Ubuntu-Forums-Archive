---
title: "screen shuts off on startup"
date: 2007-07-01
forum: General Help
---

### Post by ryanjacobson on 2007-07-01
so Im fairly new to ubuntu I've only been using it for about a month now. anyways I was messing around today and installed beryl fallowing this guide [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI)

it installed fine but when I double clicked the icon it put on my desktop my monitor just shut off. I restarted my computer and it gets to the ubuntu loading screen and then my monitor just shuts off. Is there anyways i can undo what ever I've done without losing everything?

---

### Post by PaulFr on 2007-07-01
To stop 'beryl' from auto starting, you could
1. Boot in recovery mode
2. Then remove the autostart file ```
sudo rm /etc/xdg/autostart/beryl-manager.desktop
```

Note: The guide you referenced indicates ```
sudo rm /etc/xdg/autostart/beryl-manager.desktop002
``` but I think that is a typo. Hope this helps.

---

### Post by ryanjacobson on 2007-07-01
I removed the autostart file but its still doing the same thing. any other ideas?

---

### Post by ryanjacobson on 2007-07-01
anybody??

---

### Post by PaulFr on 2007-07-01
Please see **[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)** for details on how to uninstall Beryl. (go a bit down in this section below step 10 of installation, there is a 4 step undo procedure).

---

### Post by ryanjacobson on 2007-07-01
thanks.. i just uninstalled it but to no avail. I guess im just going to have to reinstall ubuntu and learn my leson

---

