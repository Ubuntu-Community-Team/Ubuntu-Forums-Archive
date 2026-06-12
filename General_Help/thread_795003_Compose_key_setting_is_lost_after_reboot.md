---
title: "Compose key setting is lost after reboot"
date: 2008-05-15
forum: General Help
---

### Post by daehenoc on 2008-05-15
Hi all,

I've recently done an upgrade from 7.10 to 8.04 on a Dell Latitude D630.  I've noticed that after a reboot, the setting I use for the 'Compose key', the left Win-key, does not work.

However, after a reboot, I go to System -> Preferences -> Keyboard, select the Layout tab, click on the Layout Options button, and the 'Compose key position' is in bold, indicating that this option is set!  Sure enough, if I expand this option, the 'Left Win-key' option is selected, but this key doesn't operate as the Compose key until I uncheck the selection box and check it again.  Once I do this, it works fine.

After reading a few posts, I'm going to try setting this in the xorg.conf file in the default input device section and see if it sticks over reboots.

Cheers,
Greg

---

### Post by ainsworth on 2008-06-08
Exact same problem here, I find that unticking the setting and then reticking gets it going again but only until I restart. Did you find a solution?

EDIT: I'm on 8.04 AMD64 here and am also trying to set it to left win-key

---

### Post by drs305 on 2008-06-08
If you don't want to edit files, you can put an entry in Sessions, Startup. Here is what I use to change a key to the tab key:
```
xmodmap -e "keycode 112 = Tab"
```

Just substitute keys. If you don't know the key codes, an app called **xev** will let you press a key and tell you what the code is.

---

### Post by daehenoc on 2008-06-09
Yes, I got it fixed by adding the key map to the xorg.conf file manually.  I don't have the config here, but you can Google for the xorg configuration to set the mapping in the xorg.conf file.

---

