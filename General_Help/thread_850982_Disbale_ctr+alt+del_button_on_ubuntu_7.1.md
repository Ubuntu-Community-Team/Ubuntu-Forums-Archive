---
title: "Disbale ctr+alt+del button on ubuntu 7.1"
date: 2008-07-06
forum: General Help
---

### Post by Mr.Jkate on 2008-07-06
I need to disbale ctr+alt+del button on ubuntu 7.1. I modifide /etc/even.d/control-alt-delete to do nothing and rebotted my machine. 
When i pressed ctr+alt+del button, I still get prompt to log off.

Plz advise.

---

### Post by sayakb on 2008-07-06
Goto System->Preferences->Keyboard Shortcuts
Find the **Log Out** option (Under topic **Desktop**), click on where it shows Ctrl+Alt+Del and press Backspace.

---

### Post by Mr.Jkate on 2008-07-07
I need to know the name of the file where it keeps the mapping of short cut keys and commands. I need to apply this change via script rather than from GUI.

---

### Post by sayakb on 2008-07-07
Sorry, I'm not sure about the file (but I'll try and search), though I'm aware of the gconf-editor settings:
Navigate to **/apps/metacity/global_keybindings **and **/apps/metacity/keybinding_commands**.

---

### Post by Mr.Jkate on 2008-07-07
Is it possible for you to tell me the location from where I can download the source for for /usr/bin/gnome-keybinding-properties program.

---

### Post by sayakb on 2008-07-07
Do you have source repos enabled. If yes, then at a terminal:
```
sudo apt-get source gnome-control-center
```
This should include the source you need.

---

