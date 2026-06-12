---
title: "Hotkey for Terminal not Working"
date: 2019-12-07
forum: General Help
---

### Post by cyber-spock on 2019-12-07
Greetings,

The hotkey Ctrl-Alt-T, is no longer opening the Terminal. I did open the hotkey settings, and for good measure, I reset all hotkey settings, but no dice. All the other hotkeys are working except this one. 

I am running Ubuntu 18.04.

---

### Post by gurdenite on 2019-12-07
Alt+F2 gnome-terminal

---

### Post by vanadium on 2019-12-08
The easy way would be to delete the default keybinding in Settings - Keyboard Shortcuts" for "Launch Terminal" under "Launchers", and add a custom shortcut at the end of the list that executes gnome-terminal or perhaps gnome-terminal.wrapper. If you want, however, to debug what might have gone wrong in your installation, then see [https://askubuntu.com/a/1194271/558158](https://askubuntu.com/a/1194271/558158)

---

### Post by cyber-spock on 2019-12-09
Thank you Vanadium. Checking the dconf setting solved my problem.

---

