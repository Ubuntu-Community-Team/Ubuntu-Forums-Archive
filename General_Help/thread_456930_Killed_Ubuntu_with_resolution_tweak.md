---
title: "Killed Ubuntu with resolution tweak"
date: 2007-05-28
forum: General Help
---

### Post by hrvatski on 2007-05-28
I'm a total noob, and whilst blindly following internet tutorials to improve resolution, I managed to prevent Ubuntu from starting up. When I attempt to do so I get the following message:

**Failed to start the x server (your graphical interface)** etc...

I edited some file which I definitely shouldn't have, but I have no idea what it was. I just want to restore the resolution to the way it was. Even though it wasn't pretty, it worked.

Any tips would be greatly appreciated :D

---

### Post by LPomfrey on 2007-05-28
After you get that message, if I'm correct, it should leave you in a shell. You'll need to log in using your usual username and password and then type:
```
cd /etc/X11
```
To get into the directory containing the settings for X. Then type:
```
ls -l
```
To list files. There should be a few files named "xorg.conf.<string_of_numbers>" Where <string_of_numbers> is a date and time in the format YYYYMMDDHHMMSS.

Select the one from before you tried to change the resolution and type:
```
sudo cp xorg.conf.<string_of_numbers> xorg.conf
```
It will ask you to enter your password.

After this type:
```
sudo /etc/init.d/gdm restart
```
It will ask you for your password again. 
To restart the GNOME display manager (if you're using Kubuntu I think the command is ....kdm restart.)

EDIT: If those files aren't there and you edited xorg.conf with a text editor rather than using sudo dpkg-reconfigure then it might be just a file named xorg.conf~ you're looking for, if this is the case you'd do:
```
cp xorg.conf~ xorg.conf
```

---

### Post by hrvatski on 2007-05-28
holy crap, that fixed it, props to you and to ubuntu :)

---

