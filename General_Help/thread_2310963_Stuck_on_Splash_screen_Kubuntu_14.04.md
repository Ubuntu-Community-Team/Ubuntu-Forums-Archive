---
title: "Stuck on Splash screen Kubuntu 14.04"
date: 2016-01-23
forum: General Help
---

### Post by brado2 on 2016-01-23
[COLOR=#111111][FONT=Ubuntu]I can operate the terminal normally with [/FONT][/COLOR]Ctrl+Alt+F1[COLOR=#111111][FONT=Ubuntu], but [/FONT][/COLOR]Ctrl+Alt+F7[COLOR=#111111][FONT=Ubuntu] is stuck on the boot splash screen. I have 2 AMD Radeon 7850 graphics cards and I'm using the proprietary drivers, so maybe this is the issue? I don't know how to change the settings without a desktop UI, however. How can I get my system to boot to GUI normally? Any commands to run to check certain settings? I see no errors on tty1[/FONT][/COLOR]

---

### Post by Nuno_Abreu on 2016-01-23
Just wondering... What does happen if you type this to the terminal?:
```
startx
```

Post the output if something goes wrong - I suspect it can be a badly configured Xorg when drivers were installed or updated (that has happened to me before). Did that happen?

Best wishes!

---

### Post by brado2 on 2016-01-24
Here's what happened when I ran that...

---

### Post by Nuno_Abreu on 2016-01-25
Just like I suspected! It's a Xorg configuration error.

Type this in the Terminal:
```
cd /etc/X11 && sudo rm xorg.conf && Xorg -configure 
```
Don't forget the capital letter in the Xorg -configure command.

Then, type this in the Terminal again.
```
startx
```

If it still does not work, post the output of this command.
```
cat /etc/X11/xorg.conf
```

---

### Post by brado2 on 2016-01-27
I never got to the last command, because Xorg -configure dumped a core. I also 'ls''d in /etc/X11 and didnt see an xorg.conf at all. Attached is what I see


Edit: as expected, startx also dumped a core and there's still no xorg.conf in that location

---

### Post by Nuno_Abreu on 2016-01-29
Probably there is no link to the /etc/X11/xorg.conf.d folder. What is the output of:
```
ls /etc/X11/xorg.conf.d/
```

---

### Post by brado2 on 2016-01-29
Folder does not exist.

"No such file or directory"

---

