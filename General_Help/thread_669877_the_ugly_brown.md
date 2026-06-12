---
title: "the ugly brown"
date: 2008-01-16
forum: General Help
---

### Post by rob1101 on 2008-01-16
whenever i login and there is that pause after i hit enter while ubuntu is loading the screen is the ugly default brown. this just doesn't go with my theme and is just kind of obnoxious. is there anyway to fix this? and i have set my login and wallpaper background to black, still nothing changed.

---

### Post by odiseo77 on 2008-01-16
Open 'System > Administration > Login Window', got o the second tab ('Local', or something like that), locate the "Background color" item, and change it to whatever color you like.

---

### Post by rob1101 on 2008-01-16
did that still the same.

---

### Post by yabbadabbadont on 2008-01-16
You may have to restart GDM (the graphical login screen) before the change takes effect.  Logout then hit Control-Alt-Backspace to kill the Xserver.  That will force GDM to restart.  (or just reboot)

---

### Post by matthinckley on 2008-01-20
I have the same issue.. both GDM and wallpaper are set to black backgrounds.. several reboots and still have the brown background during login

---

### Post by PurposeOfReason on 2008-01-20
[http://ubuntuforums.org/showpost.php?p=752855&postcount=12](http://ubuntuforums.org/showpost.php?p=752855&postcount=12)

I believe that is what I did when I used Ubuntu. I know I had to edit some /etc file.

---

### Post by matthinckley on 2008-01-20
wow that was really fast!

I found another fix here:
[http://ubuntuforums.org/showpost.php?p=4024549&postcount=2](http://ubuntuforums.org/showpost.php?p=4024549&postcount=2)

---

### Post by PurposeOfReason on 2008-01-20
> **matthinckley said:**
> wow that was really fast!

I found another fix here:
[http://ubuntuforums.org/showpost.php?p=4024549&postcount=2](http://ubuntuforums.org/showpost.php?p=4024549&postcount=2)

Thats the one I was looking for. .I think.

---

### Post by rob1101 on 2008-01-20
i looked at both of those solutions and i don't have either of those files...

EDIT: NVM i was looking in the wrong place

---

