---
title: "Application item from menu bar does't respond"
date: 2007-05-25
forum: General Help
---

### Post by syllepsa on 2007-05-25
Hi,

Does anyone can help me with the following problem:
After 5 days of using  Ubuntu (installed via Wubi) Application item from menu bar doesn't respond. Places and System work fine.

I would be grateful for any response. I should mention that I am newbie as far as goes linux.

Mariusz

---

### Post by forestG on 2010-10-24
Hi! have you tried the right-click option to edit the menu? another workaround is to remove and add this panel again or add the main menu panel. Just click on the top panel or the bottom one the choose add panel and then search for the main menu panel to add.

---

### Post by aeronutt on 2010-10-24
You may want to try resetting the panels also. I've found this method works well:

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html]("http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html")

Open a terminal, and run the following 3 commands:

```

gconftool &#8211; -recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

