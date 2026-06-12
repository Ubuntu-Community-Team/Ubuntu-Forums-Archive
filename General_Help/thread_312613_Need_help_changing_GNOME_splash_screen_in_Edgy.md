---
title: "Need help changing GNOME splash screen in Edgy"
date: 2006-12-04
forum: General Help
---

### Post by threethirty on 2006-12-04
I went into the Configuration Editor.  I went to schemas -> apps -> gnome-session -> options and tried to change splash-image and I got this error.

```
Currently pairs abd schemas can't be edited.
This will be changed in a later version.
```

any help is awsome](*,)

---

### Post by bapoumba on 2006-12-04
Hi, should be > apps > gnome-session > option > splash_image. Not tried though ;)

---

### Post by threethirty on 2006-12-04
](*,) :-k 

ok I went to the right place this time changed the value and nothing.

I was following [this guide ]("http://www.ubuntuforums.org/showthread.php?t=11478") and when I restarted GNOME nothing changed.

is there somewayt to save in the Config tool that I'm missing or is it something else.

---

### Post by endersshadow on 2006-12-04
Take the easy way out!

[list]
[*] In the terminal, type:
```
sudo apt-get install gnome-splaschscreen-manager
```

[*] Go to System>Preferences>Splash Screen

[*] Change to your heart's content!

[*] ????

[*] Profit!
[/list]

---

### Post by threethirty on 2006-12-04
What am I doing wrong, I have the above mentioned prog installed and I loaded my new splash, but still isnt working

I have a screenshot attached to make sure everything is good.

---

### Post by threethirty on 2006-12-04
nevermind i got it thanks everyone

---

### Post by strabes on 2006-12-04
from [http://ubuntuforums.org/showthread.php?t=24415](http://ubuntuforums.org/showthread.php?t=24415)

Splash screens are stored in their own special directory, so the commands are slightly different.
1) "$ cd /usr/share/pixmaps/splash"
2) "$ sudo mv ~/Desktop/file_goes_here ."
3) Repeat #2 for all extracted files

This is for dapper so may not work in edgy.

---

