---
title: "Remove Rhythmbox noitfication area icon"
date: 2007-12-19
forum: General Help
---

### Post by weinreis on 2007-12-19
Is there a way to remove the Rhythmbox notification area icon? Is there any way to limit which apps show up in the notification area? I know this is kind of an odd question. Thanks.

---

### Post by p_quarles on 2007-12-19
I'm sure there is a way, but I don't use Rhythmbox myself, so I can't tell you exactly how. I can, however, make a few educated guesses:
1) Many apps have an option in Settings/Preferences/Configuration that allows you to turn the system tray icon on and off. 

2) Some apps have a plaintext configuration file in your home folder. Try to find this by opening your home folder, selecting "show hidden files," entering the .rhythmbox directory, and looking for any potential settings files. It could be as simple as changing one of the options from "True" to "False."

3) If both of those fail, the icon is probably set in gconf. Open up the gconf editor by pressing alt-F2 and typing
```
gconf-editor
```
This can be a confusing tool to use if you haven't before, but you're looking for entries related to the desktop and Rhythmbox. There should be a setting somewhere in there that allows you turn the icon on or off.

---

### Post by weinreis on 2007-12-19
Yeah, I've tried all three of those things, and I just can't seem to find it.

---

### Post by strabes on 2008-02-16
Bump. I'd like to know if this is possible too. I don't like how when windows are open for some applications they have a system tray icon and others don't. It's not consistent interface design and makes it harder on newer users.

---

### Post by strabes on 2008-04-26
Bump

---

### Post by strabes on 2008-05-07
Bump

---

