---
title: "Key Bindings"
date: 2008-04-18
forum: General Help
---

### Post by _Nate_ on 2008-04-18
I was wondering how to map a certain set of key presses to a single key press. Namely, I have a keyboard in which many F* buttons do not work and I would like to remap <Super> + 1 to F1, <Super> + 2 to F2, and so on. How is this done? I couldn't seem to find an easy way to do this with xmodmap.

---

### Post by ryanhaigh on 2008-04-19
Create some bash scripts using xte (from the package xautomation) to simulate key presses.
eg 
```

#!/bin/bash
xte "key F1"

```
Save that file as ~/.typeF1.sh for example. (the . makes it hidden)

You can then use gconf-editor and assign these scripts as metacity commands /apps/metacity/keybinding_commands (the command to enter would be /home/yourusername/.typeF1.sh) and then assign keybindings to those command using gconf-editor under /apps/metacity/global_keybindings. Note that if you are using compiz you can do the same with the advanced settings application under general settings.

---

### Post by _Nate_ on 2008-04-19
I did this, and the script works when I run it from the terminal, but it doesn't work when I run it from a gconf-editor global keybinding. I have <Super>1 bound to run_command_1, and in  keybinding_commands ! have command_1 bound to ~/KeyboardConfig/.typeF1.sh (which will cause an F1 press when run from the terminal), but when I press <Super>1, nothing happens. If, however, I change command_1 to something like 'gnome-terminal', the terminal will open when I press <Super>1, so it appears as if gconf-editor simply does not want to run .typeF1.sh. What's going on?

---

### Post by ryanhaigh on 2008-04-19
I don't know if you can use shell expansion like ~/ for the command, you are probably better off using the full path /home/username/file.sh You could also try using the full path to xte which is /usr/bin/xte

---

### Post by ryanhaigh on 2008-04-19
I don't know if you can use shell expansion like ~/ for the command, you are probably better off using the full path /home/username/file.sh You could also try using the full path to xte which is /usr/bin/xte

You could also try installing [apt://gnome-osd](apt://gnome-osd) and then adding a line to your script like 
```

#!/bin/bash
/usr/bin/xte "key F1" &&
/usr/bin/gnome-osd-client "Pressed F1" &&
exit

```

---

### Post by HermanAB on 2008-04-19
xbindkeys?

---

