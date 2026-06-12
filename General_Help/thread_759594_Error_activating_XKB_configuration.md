---
title: "Error activating XKB configuration"
date: 2008-04-19
forum: General Help
---

### Post by Aquastus on 2008-04-19
Hello. I had the following error message on login:

```
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
```

Results of xprop -root | grep XKB
```
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "est", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "est", "", ""
```

Results of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
```
 layouts = [est,ee]
 model = 
 options = [grp	grp:alts_toggle]
 overrideSettings = true
```

First of all, what does this even mean? And what am I supposed to do?

---

### Post by rgrig on 2008-05-01
Same error here after upgrading to 8.04. The output for me is:
```

_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "gb", "", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "gb", "", "lv3:ralt_switch"

```

and 
```

 layouts = [gb,ro	std]
 model = thinkpadintl
 options = [lv3	lv3:ralt_switch,grp	grp:shifts_toggle]
 overrideSettings = true

```

---

### Post by flaggh on 2008-05-02
Same problem here:
```
harlan@harlan-macbook:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "mac", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us", "mac", "lv3:ralt_switch"
harlan@harlan-macbook:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = macbook78
 overrideSettings = true
 options = []

```

---

### Post by rgrig on 2008-05-02
I removed and added again the Romanian keyboard and now the error doesn't appear anymore.

---

### Post by Zsola on 2008-05-02
Same problem here. I ve got hungarian keyboard layout, and the error only appear with one of my other user account. Tried to delete it and then create an other but still ended up with the same error message. Any hints on this? Thx.

---

### Post by firedevilbg on 2008-05-16
And I have this problem... I have a Bulgarian Phonetic layout and it doesn't work... Does anybody know how to fix that?

---

### Post by naoli on 2008-05-29
Problem solved by going into gconf

desktop > gnome  > peripherals > keyboard > general > host_computer > kbd

Then edit "layouts" and "options" and del everything.

Then you can set up a new keyboard in System, pref, keyboard.

;)

---

