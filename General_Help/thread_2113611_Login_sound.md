---
title: "Login sound"
date: 2013-02-07
forum: General Help
---

### Post by Synoc on 2013-02-07
I want to disable the login sound. However, the login screen does not appear in preferences, system tools, or administration. I saw a page that said you could disable in in lightDM but muting that mutes everything when DO log in. so no joy there. Where is my configuration for that now?

Also while I'm at it. why does google chrome always put my close, min, and max buttons on the left even though I have them on the right?

---

### Post by fantab on 2013-02-08
You can disable it from "Startup Applications".  Just un-check the 'GNOME Login Sound'. If, you don't see ALL the startup/autostart applications in the Startup Manager then run the following from the Terminal:

```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```

EDIT: For chrome: in chrome settings you have to choose from "Appearance"  to "Use system title bar and borders" for your customizations to work.

---

### Post by Synoc on 2013-02-08
> **fantab said:**
> You can disable it from "Startup Applications".  Just un-check the 'GNOME Login Sound'. If, you don't see ALL the startup/autostart applications in the Startup Manager then run the following from the Terminal:

```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```

EDIT: For chrome: in chrome settings you have to choose from "Appearance"  to "Use system title bar and borders" for your customizations to work.

I don't want the system title bars I want the ones used with the theme I have, but even the theme ones are on the right... and all of my other Linux systems. Theses are always on the left for some reason. the theme is Ancient Dark. if you look at the screen shots they are on the right. on my Ubuntu desktop they are on the right too. on this PC before I nuked it and installed 12.04 they were on the right as well.

As far as the login sound GNOME Login Sound was not there, so I just renamed the file so it doesn't find it any more, but thanks anyway.

---

