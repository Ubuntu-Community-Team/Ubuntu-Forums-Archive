---
title: "Problem log on to gnome"
date: 2008-06-26
forum: General Help
---

### Post by look2 on 2008-06-26
I reinstalled hardy yesterday and all worked fine. 
Installed all the apps I want to use and just to be safe I reeboted the system. When starting the system I get the login screen, I log on the the system and hears the startupsound and my background image appears. And then... nothing... 

I can rightclick and access that meny, change background image and so on, but nothing more, I can't see any panels and stuff like that...

---

### Post by PmDematagoda on 2008-06-26
When you reach the login screen press Options>Sessions and select GNOME Fail Safe, see if that allows you to login properly.

---

### Post by look2 on 2008-06-26
Won't work, getting the same problem. 
Have tried to restart gnome with ctrl+alt+backspace and also tried to restart the whole system with the same result.

---

### Post by VMC on 2008-06-26
Maybe create a new user would work.

IF you drop to Terminal with Ctrl+Alt+F1, then 'ps _A|less' , to investigate what's not running. Or even 'dmesg' and look for error messages. Maybe gnome-panel listing on your 'ps' output.

---

