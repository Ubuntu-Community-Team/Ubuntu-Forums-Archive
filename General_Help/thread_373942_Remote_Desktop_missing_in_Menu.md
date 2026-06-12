---
title: "Remote Desktop missing in Menu"
date: 2007-03-01
forum: General Help
---

### Post by ttleser on 2007-03-01
Hello all. I'm a newbie at using Linux so please bear with me.

I'm running Xubuntu using Gnome as my desktop. On an older built computer using Xubuntu and Gnome as the desktop I can find Remote Desktop under System > Preferences. On the newly built computer it's missing.

Thoughts?

---

### Post by megamania on 2007-03-02
> **ttleser said:**
> I'm running Xubuntu using Gnome as my desktop. On an older built computer using Xubuntu and Gnome as the desktop I can find Remote Desktop under System > Preferences. On the newly built computer it's missing.

Thoughts?
I'm not at home now so I can't check myself, but I think you have to look for something like "menu editor" - some menu entries are hidden and you need to enable them. Hope that helps.

---

### Post by tbodine on 2007-03-02
I really don't understand why you're using GNOME as you desktop on a Xubuntu install, why not just use Ubuntu(which comes with GNOME by default, rather than Xfce)?
Anyways, if it is in fact installed, you should be able to right click the menu, and select "Edit Menus" and from there look in the sub-menu's for where you believe it should be, it should be in one of them -- I had to install my own Remote Desktop Client, but I had Terminal Server Client in the Internet sub-menu.
I hope this helps, if you want to install Remote Desktop Client, the one that I have, try the following in the command line:
```
sudo apt-get install grdesktop
```

---

### Post by ttleser on 2007-03-03
> I really don't understand why you're using GNOME as you desktop on a Xubuntu install, why not just use Ubuntu(which comes with GNOME by default, rather than Xfce)?
Anyways, if it is in fact installed, you should be able to right click the menu, and select "Edit Menus" and from there look in the sub-menu's for where you believe it should be, it should be in one of them -- I had to install my own Remote Desktop Client, but I had Terminal Server Client in the Internet sub-menu.
I hope this helps, if you want to install Remote Desktop Client, the one that I have, try the following in the command line:

Code:
sudo apt-get install grdesktop

Ran this, but didn't see any addition to any menu for any "new" program.

Also, I tried editing the menus to make sure Remote Desktop wasn't hiding. It's just not there.

As for not using Ubuntu, I originally loaded Xubuntu instead of Ubuntu because I was loading it on an older system and kinda learned a little of Linux on that. I was originally getting it setup for LTSP, but the LTSP instructions are based around Gnome. I didn't really want to experiment until I learned Linux a little more. But I'm also having problems not getting XDMCP to stay enabled, so maybe I should just load Ubuntu instead. :(

---

