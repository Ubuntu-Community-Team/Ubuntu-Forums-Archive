---
title: "can not find wubi registry keys..."
date: 2007-05-17
forum: General Help
---

### Post by blackjackel on 2007-05-17
This is odd, I had trouble with resizing so I had to reinstall and now I can not find the wubi registry keys... I searched the registry for wubi and simply can not find the key location, could you possibly post them here?

---

### Post by alliantdevil on 2007-05-17
the key in windows should be somewhere under hkey current user>software then in a "folder" either named wubi or cutlersoftware. but that's just from my own assumptions since i havent used windows in quite some time.

---

### Post by blackjackel on 2007-05-17
I found a key that seems to point to where the wubi registry keys are, but they aren't there...

My Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Wubi


this key is in HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\Currentversion\Applets\Regedit\ and the key is titled "lastkey" a REG_SZ value.

Maybe that will help?

---

### Post by blackjackel on 2007-05-17
Update:

I tried CREATING a key called wubi but I got an error that it already exists... strange? Its not listed.... so....I restarted regedit and the key magically re-appeared.

It is in the key location posted above just as it should have been.

This is part of the reason why I want to switch to linux... :/

---

### Post by ecology2007 on 2007-05-17
All the keys for current wubi version are located in
"HKLM "Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi"
Do you have admin rights for your windows account ?
What is the exact version of your OS ?
How many network cards do you have ?

---

### Post by anotherbigal on 2008-08-22
Does anyone know if the un-install option actually removes the registry entries?

---

