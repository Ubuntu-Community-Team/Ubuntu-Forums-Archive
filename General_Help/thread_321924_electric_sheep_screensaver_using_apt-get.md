---
title: "electric sheep screensaver using apt-get?"
date: 2006-12-19
forum: General Help
---

### Post by Fittersman on 2006-12-19
IS there any way i can get the electric sheep screensaver on ubuntu using apt-get or the terminal?

i have done some googling but i honestly just dont get how to install a .tar.gz package... i just dont get it.

and i dont know how to use the terminal to get stuff and download things either.

[http://electricsheep.org/](http://electricsheep.org/)

---

### Post by Azakus on 2006-12-19
Don't worry, this screensaver is included in Ubuntu's repos. Just open the terminal and paste in this code:
```
sudo aptitude install electricsheep
```

---

### Post by Fittersman on 2006-12-19
how do i change my screensaver to it now? i cant find it in the screensaver place.

---

### Post by majoridiot on 2006-12-19
from the main menu panel:

System-->Preferences-->Screensaver

---

### Post by Fittersman on 2006-12-19
went there but its not listed.

---

### Post by Fittersman on 2006-12-20
anyone know how to get this screensaver listed in the screensaver place as mentioned above?

---

### Post by Azakus on 2006-12-20
Aha! Found a similar thread to this one. Turns out that gnomescreensaver (the default Ubuntu screensaver) doesn't like Electric Sheep and won't display it. You have to replace it with Xscreensaver, then it will work.
[HOWTO:Replace gnome-screensaver with xscreensaver]("http://www.ubuntuforums.org/showthread.php?t=195557&highlight=replace+screensaver")

---

### Post by riven0 on 2006-12-20
> **Azakus said:**
> Aha! Found a similar thread to this one. Turns out that gnomescreensaver (the default Ubuntu screensaver) doesn't like Electric Sheep and won't display it. You have to replace it with Xscreensaver, then it will work.
[HOWTO:Replace gnome-screensaver with xscreensaver]("http://www.ubuntuforums.org/showthread.php?t=195557&highlight=replace+screensaver")

Ah! That's the howto I was looking for. Thanks. :KS

---

### Post by Fittersman on 2007-01-06
sorry for such a late reply, but when the screensaver comes up it says something along these lines:

'read only process, ie. disabling downloading process'

and right under that it says:

'downloading the first sheep...'

its been downloading for a long time and it never starts the actual screensaver... so i dont know what to do.

if theres a way to take a picture of the screensaver someone should tell me because it just quits it when i try, that might give a better clue as to what is goin on.

(it a black screen with yellow typing)

---

