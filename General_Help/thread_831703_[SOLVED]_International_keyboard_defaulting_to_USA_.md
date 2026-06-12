---
title: "[SOLVED] International keyboard defaulting to USA layout"
date: 2008-06-17
forum: General Help
---

### Post by Pi72 on 2008-06-17
Hello everyone.

I am using Ubuntu Hardy 8.04 64bit with an international keyboard. Past friday I got a new box, and I did a fresh reinstall of everything. Suddenly the keyboard started to act strange. After 3 hours of tinkering with keyboard settings and googling, I discovered that it was simply the keyboard which somehow broke (it was the only really old piece of my computer).

Next day I got a new keyboard, spanish layout. I plugged it in and it was in USA layout. I went to System->Preferences->Keyboard->Layout and the only one I had there was Spanish; yet the keyboard behaved as if it was an USA keyboard. I readded the spanish layout, deleted the old layout, and everything was working fine.

However, everytime I reboot, I keep having an USA layout, which is the system default, as if I had selected nothing in the layout list. I must go to the keyboard settings to do the same steps again and again: readd the spanish layout, delete the other. Otherwise I can't use the keyboard normally. I can't seem to solve it, I must have broken something while tinkering with the old keyboard but I don't know what. I've tried changing the keyboard type (currently PC generic 105 keys intl), and other stuff. I don't want to do a reinstall *again* (I did 3 just this weekend). Any ideas?

---

### Post by Pjotr123 on 2008-06-17
Do this:
Applications - Accessories - Terminal
copy/paste this line:
```
gksudo gedit /etc/X11/xorg.conf
```

Press Enter.

In this configuration file, delete the *first* Section "Input device" and replace it with this text (use copy/paste):
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

```

Save and close the file. Now do a complete reboot of your computer. Evereything should work fine now.  :-)

---

### Post by Pi72 on 2008-06-17
Thanks, that solved it. My nVidia settings went to hell, so I had to reinstall them with EnvyNG. But the keyboard works well again, thanks a lot. Look, an eñe --> Ñ :)

---

