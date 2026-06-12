---
title: "Hotkeys"
date: 2007-11-05
forum: General Help
---

### Post by zouriel on 2007-11-05
There is an app for M$ called Keyboard Express, Easy Macro Recorder and ........

where u can setup canned text to a hotkey..... I havent been able to find on for *nix anyone know of one?

---

### Post by rbo83 on 2007-11-06
If you want to do it while under Gnome or KDE, use the Keyboarb menu options in the Preferences. If you are using it in the Terminal mode (or command line), you can use the loadkeys program to set the value of keys at boot time through the /etc/rc.local script. You can chack the man page (man loadkeys) to see how it works. The easy way to do it is to
use the kernel string table is a sequence of strings with names like F31. One can make function key F5 (on an  ordinary  PC  keyboard) produce the text ‘Hello!’, and Shift+F5 ‘Goodbye!’ using lines

              keycode 63 = F70 F71
              string F70 = "Hello!"
              string F71 = "Goodbye!"

---

