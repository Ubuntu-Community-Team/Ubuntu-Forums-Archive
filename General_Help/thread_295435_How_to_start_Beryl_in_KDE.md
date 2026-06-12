---
title: "How to start Beryl in KDE"
date: 2006-11-08
forum: General Help
---

### Post by krypto_wizard on 2006-11-08
I have nVidia FX5500 and using latest released nVidia drivers I could start beryl in gnome.

I installed Kiba-dock and I guess it will only work in KDE ...rite ?


How can I add beryl in KDE and ensure it loads up at startup time.

Please help.

---

### Post by vidak on 2006-11-08
Does it work if it you put a symlink to beryl into .kde/Autostart?

---

### Post by krypto_wizard on 2006-11-08
I have two files in ~/.kde/Autostart

beryl.start 
```

[Desktop Entry]
Encoding=UTF-8
Exec=beryl-manager
GenericName[en_US]=
StartupNotify=false
Terminal=false
TerminalOptions=
Type=Application
X-KDE-autostart-after=kdesktop

```

xmodmap.sh
```

xmodmap /usr/share/xmodmap/xmodmap.us
xmodmap -e "keycode 22 = BackSpac

```


Still it doesn't start automatically. I goto konsole and then type
```

beryl-manager

```

Then it comes on.


Please help how to make it autostart.

Also please tell me the option to disable it from Autostart if needed

Thanks

---

