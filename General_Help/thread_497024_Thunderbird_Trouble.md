---
title: "Thunderbird Trouble"
date: 2007-07-09
forum: General Help
---

### Post by pbhill on 2007-07-09
Can anyone tell me what is causing this error message whenever I try to start Mozilla Thunderbird? It had been working just fine.

        "Mozilla-Thunderbird is already running but not responding. To open a new window you must first close the existing Mozilla-Thunderbird process or restart your system. "

It isn't running, and restarting doesn't solve the problem. Any ideas? 
Thanks.

---

### Post by scorpion_gr on 2007-07-10
When I get such messages for mozilla applications (thunderbird,firefox) I bring up the process manager and kill the application manually. Sometimes mozillas keep running even after you close all windows, so you gotta kill em.

---

### Post by pbhill on 2007-07-10
Well, I checked there, and nothing indicates that Thunderbird is running in the background.  I uninstalled and reinstalled the application, but get the same message.  Thanks anyway.

---

### Post by Rui Pais on 2007-07-10
try:
```
mkdir .mozilla-thunderbird/BAKUP
mv .mozilla-thunderbird/*.default .mozilla-thunderbird/BAKUP/
```
and then launch thunderbird.
If it work you need to recover you mail by copying the folder Mail on BAKUP/ to the new default profile.

---

### Post by flipflopnick on 2007-08-04
"Thunderbird is already running, and is not responding" error message cure.
Thanx to posters above. Common error to any OS.
You need to create a new profile for Thunderbird, because old one is corrupt.

open menu editor in System, Preferences, Main Menu (not Menus and Toolbars)
Find Internet on left
Tick box for Thunderbird Profile Manager on right
close editor

Start Thunderbird Profile manger
Create new Profile.
Restart Thunderbird.
Cancel new account creation and restore your Thunderbird files. 
restore info on Mozilla.com
basically copy files across

HTH

---

### Post by apetresc on 2007-08-04
> **flipflopnick said:**
> "Thunderbird is already running, and is not responding" error message cure.
Thanx to posters above. Common error to any OS.
You need to create a new profile for Thunderbird, because old one is corrupt.

open menu editor in System, Preferences, Main Menu (not Menus and Toolbars)
Find Internet on left
Tick box for Thunderbird Profile Manager on right
close editor

Start Thunderbird Profile manger
Create new Profile.
Restart Thunderbird.
Cancel new account creation and restore your Thunderbird files. 
restore info on Mozilla.com
basically copy files across

HTH
flipflopnick's advice should work, but for the record, here's a much easier way of getting to the profile manager: ```
mozilla-thunderbird -ProfileManager
```

---

