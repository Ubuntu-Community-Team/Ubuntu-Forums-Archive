---
title: "Xscreensaver in Ubuntu 13.10 &amp; Trusty 14.04"
date: 2014-02-03
forum: General Help
---

### Post by Redalien0304 on 2014-02-03
Can you Install Xsceensaver & Extras in Saicy or Trusty?? Do you or Can you Remove gnome screesaver? Google Search is a mixed bag of reusults. I am also running Ciinnamon Nightly if it matters.  Thanks

---

### Post by Dennis N on 2014-02-03
I have both xscreensaver and gnome-screensaver installed in Ubuntu 12.04. gnome-screensaver is disabled in startup applications (where it is called 'screensaver'), and xscreensaver was installed and added to my startup applications (as xscreensaver). This works in 12.04. You could try this in your 13.10 or 14.04 system and see if it works out there as well.

---

### Post by Bashing-om on 2014-02-03
Redalien0304; Hi !

Addition: I have xscreensaver installed (works great ) on 13.10/xfce4 .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by Dennis N on 2014-02-03
Two additional things:

**Startup Applications** dialog may not show all the startup applications. In Ubuntu 12.04, it doesn't, and it was necessary to run this command:

```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```

If you add xscreensaver to the startup applications, the command you need is [FONT=Courier New]**xscreensaver -no-splash**[/FONT]

---

### Post by ajgreeny on 2014-02-03
It works fine in Xubuntu trusty 14.04, just as it does in 12.04.

---

### Post by Redalien0304 on 2014-02-04
Thanks all problem solved now. I installed Xcreensaver & Uninstalled Gnome screensaver. Ubuntu 14.04 Trusty that is.

---

### Post by robsbkai on 2014-09-19
ajgreeny, can you tell me which commands you use for the terminal ?

and when I have installed Xscreensaver , where can I find it ?

Robert.

---

