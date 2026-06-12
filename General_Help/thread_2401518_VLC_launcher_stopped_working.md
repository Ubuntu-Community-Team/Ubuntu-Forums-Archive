---
title: "VLC launcher stopped working"
date: 2018-09-19
forum: General Help
---

### Post by No_I_wont on 2018-09-19
Nothing happens when trying to start VLC from the launcher. 
Worked a while ago.
Starting with "vlc" in terminal works.
Tried to reinstall but it doesn't help. 

Where are the launcher file located? It's not in ~/.local/share/applications/

---

### Post by Holger_Gehrke on 2018-09-19
That should be '/usr/share/applications/vlc.desktop'. The directory '/usr/share/applications/' is for the system wide starters while '~/.local/share/applications/' is for your personal ones (if you have programs installed under your $HOME or wnat to start a program with specific options). To find the starter for a program you can use grep like this:```
grep -l 'text to search for' /usr/share/applications/*.desktop ~/.local/share/applications/*.desktop
```replace 'text to search for' with something you expect to be in the desktop-file (the name of the executable or part of the text shown in the menu or on the starter).

Holger

---

### Post by No_I_wont on 2018-09-19
Thank you.

That seems to be in order though.
Exec=/usr/bin/vlc --started-from-file %U
TryExec=/usr/bin/vlc

Any idea what might be stopping the launcher from working?
VLC is the only program that doesn't start. It does work in terminal.
Can I get a log file for the launcher somehow?

---

