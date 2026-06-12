---
title: "Change the keyboard's language on login screen"
date: 2008-01-10
forum: General Help
---

### Post by MrTre1z3 on 2008-01-10
Hello everybody.

I formated my computer recently. I installed ubuntu again but this time, it didn't ask me to choose my keyboard type during the installation. So when I finished to install it, my keyboard was in french because I chose to have my system in french. The problem is that I don't want it to be in french. I already changed the language through system->Preferences->keyboard to portuguese and in fact my keyboard is now well configured except on the Login screen where it remains in french. My question is: How can I fix it ?
I appreciate any help. Thanks in advance.

---

### Post by rubicon on 2008-01-10
You need to reconfigure your xserver: ```
sudo dpkg-reconfigure xserver-xorg
``` or ```
sudo dpkg-reconfigure -plow xserver-xorg
```

If this won't work, try editing config file maunally: ```
sudo nano /etc/X11/xorg.conf
```
Mine look like this:
```

*<cut>*
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,ru"
	Option		"XkbVariant"	",winkeys"
	Option		"XkbOptions"	"grp:ctrl_shift_toggle,grp_led:scroll"
EndSection
*<cut>*

```

---

### Post by rubicon on 2008-01-10
Oh, and -- to be sure -- please make backup of your xorg.conf before editing :)

---

### Post by jocko on 2008-01-10
I guess you need to set the correct keyboard layout in xorg.conf:
Run this command in a terminal:```

gksudo gedit /etc/X11/xorg.conf
```Find a section that looks something like this:
```
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "[COLOR=Red]fr[/COLOR]"
EndSection
```
Change the country code from "[COLOR=Red]fr[/COLOR]" to "[COLOR=Red]pt[/COLOR]" (if you want to change from French to Portuguese), save the file and restart the xserver (ctrl+alt+backspace).

---

