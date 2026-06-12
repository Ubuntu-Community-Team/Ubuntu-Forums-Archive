---
title: "i think i killed linux"
date: 2007-07-03
forum: General Help
---

### Post by RabidDog1 on 2007-07-03
hey guys i have a problem.. i turned my computer off last night after waiting about 10mins at the closing down screen of ubuntu.. now i have killed it. when i start it up just after the ubuntu loading screen. it comes up a blue screen and says. "Server authorization directory (daemon/ServAuthDir) is set to /var/lib/GDM but this does not exist".. now when i press ok.. it comes up to a non graphical login screen.. then all i get is like a DOS mode and im pretty sure its the Terminal... so is there a way to fix this? can i reinstall ubuntu without losing all my stuff that i have install on it?

---

### Post by gjtoth on 2007-07-03
> **RabidDog1 said:**
> hey guys i have a problem.. i turned my computer off last night after waiting about 10mins at the closing down screen of ubuntu.. now i have killed it. when i start it up just after the ubuntu loading screen. it comes up a blue screen and says. "Server authorization directory (daemon/ServAuthDir) is set to /var/lib/GDM but this does not exist".. now when i press ok.. it comes up to a non graphical login screen.. then all i get is like a DOS mode and im pretty sure its the Terminal... so is there a way to fix this? can i reinstall ubuntu without losing all my stuff that i have install on it?

GDM=Gnome Desktop Manager.  You may have killed the GDM.  I'm not sure how to reinstall it.  I'm sure someone more knowledgeable will be along to give you instructions for that.  It's *probably* a simple fix.  I just don't know EXACTLY what it is.  I learned one thing about Ubuntu:  Only reinstall as a last ditch resolution!  There have been times when I thought I really trashed it only to boot with a live CD, ask what  I should do here on the forums and get a simple answer from some of the absolute wizards on here.  No... don't reinstall.  You WILL lose your stuff!

---

### Post by RabidDog1 on 2007-07-03
thanks buddy. yea hopefully i can fix the problem without resorting to reinstal.

---

### Post by FuturePilot on 2007-07-03
Sign in and try ```
sudo dpkg-reconfigure gdm
```

---

### Post by RabidDog1 on 2007-07-03
tryed that it didnt work..i think ive stuffed it big time.. but i cant understand why it would do this only because i turned it off instead of waiting for it to
i got the error "Sudo /etc/sudoers is mode 0660, should be 0440" after i type sudo dpkg-reconfigure GDM
then it went to the promt again and then said... "sendmail fatal oper /etc/postfix/main.conf no such file or directory

---

### Post by Feba on 2007-07-03
> i think i killed linux

trust me, MS has been barking up that tree for nigh on a decade now, if a multibillion dollar company hasn't done it yet, neither have you.

I wonder if you could try launching with KDE?

---

### Post by scxtt on 2007-07-03
i'd reboot into recovery mode and do: **chmod 0440 /etc/sudoers** and try **sudo dpkg-reconfigure gdm** again ...

---

### Post by RabidDog1 on 2007-07-04
> **Feba said:**
> trust me, MS has been barking up that tree for nigh on a decade now, if a multibillion dollar company hasn't done it yet, neither have you.

I wonder if you could try launching with KDE?

well maybe they should employ me, because i think i have succeeded.:D
i CHMod the DIR to 0440. then i did the sudo dpkg-reconfigure and it looked like it was loading or something.. then it went back to the prompt so i restarted it and the same thing happened.

---

### Post by FuturePilot on 2007-07-04
Perhaps ```
sudo apt-get remove --purge gdm
```
That will probably also remove the ubuntu-desktop package as well, but don't worry, the next step will get it back as well as GDM
```
sudo apt-get install ubuntu-desktop gdm
```

---

### Post by RabidDog1 on 2007-07-04
nope still no go. this is starting to piss me off. i did them both and it installed it again but still wonts start up. anymore ideas?

---

### Post by RabidDog1 on 2007-07-04
well im on ubuntu now.. im running KDE but even KDE is missing a few things. but id rather use GDM.. this is really weird. anyhting i can try

---

### Post by scxtt on 2007-07-04
you shouldn't need a display manager to get into an X session ... type "startx" after you login to a terminal and see what happens ...

---

### Post by RabidDog1 on 2007-07-04
well i type "startx" and i think it has started KDE.. but when it loaded up t said.. "INTERNAL ERROR
FAILED TO INITIALISE HAL" and there are no icons next to the menu items.. but its still half working lol

---

### Post by kvonb on 2007-07-04
Does the LiveCD work ok?

Scan your hard drive for bad sectors, and also look on the mainboard for "popped" capacitors.

It sounds like a hardware failure to me.

---

### Post by RabidDog1 on 2007-07-04
live cd works fine.. i dont think its a hardware issue..

---

### Post by scxtt on 2007-07-04
> **RabidDog1 said:**
> well i type "startx" and i think it has started KDE.. but when it loaded up t said.. "INTERNAL ERROR
FAILED TO INITIALISE HAL" and there are no icons next to the menu items.. but its still half working loli'm not sure how *ubuntu handles HAL (hardware abstraction layer) - in gentoo i can start/stop it via **sudo /etc/init.d/hald {start/stop}** ... that'll take care of the lack of icons on the desktop, CDs not automounting, etc. ...

edit: looks like it tied in w/ dbus, so do **sudo /etc/init.d/dbus status** and see if it's running ...

---

