---
title: "Delete Key Woes"
date: 2007-02-09
forum: General Help
---

### Post by skwishybug on 2007-02-09
A new issue has cropped up for me recently on my laptop.
 
Recently updated from Dapper to Edgy and somewhere along the way my delete key has stopped doing what it is supposed to (delete things).
 
I've looked over the other posts that relate to this type of problem and they don't quite fit the probelm I am having.
 
::Setup::
Keyboard setting: Generic 104 (default offered by setup, no other listed matches what I have)
Layout: US English
System: HP Pavillion dv1000 Laptop
 
::Symptoms::
After booting, when trying to delete using the delete key, nothing happens.
 
If I go to the keyboard settings under Preferences and change the Keyboard setting to anything, and then back to default, the delete key works.
 
If I reboot, I go back to it not working.
 
::Things Tried::
I've found reference to resetting the global key-bindings, I've looked into this on my system and there is nothing assigned to the command_9 (what has been said to be the delete key). When I check after doing the change keyboard settings, there is still nothing assigned to that key.
 
Any ideas or help would be greatly appreciated

---

### Post by ingo on 2007-02-10
While I don't know the exact fix I can tell you that X gets it info for the keyboard from /etc/X11/xorg.conf

You might want to check whether your delete key works when logging into a shell rather than gnome/kde. If it does, xorg.conf is your problem. If it does not, no idea :(

---

