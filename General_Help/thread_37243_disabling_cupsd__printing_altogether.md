---
title: "disabling cupsd / printing altogether?"
date: 2005-05-26
forum: General Help
---

### Post by 23meg on 2005-05-26
i don't have a printer, am not planning to get one in any forseeable future and thus i believe have no use for cupsd. however, when i disable it using ubuntu bootup manager, gnome hangs at startup. is this not the best way to disable it? or maybe is it needed by other system components and shouldn't be disabled at all?

---

### Post by Moobert on 2005-05-26
sudo chmod -x /etc/init.d/cupsys

this will give an error on boot, but it will stop cups loading...

'+x' to reurn it back to normal, and theres always apt-get remove I guess.

---

### Post by boarder on 2007-12-14
I have disabled cupsys with the chmod method and now ubuntu starts but when I log into the gui I just get the background with no menus or anything else.  Any one have any ideas how I can fix this.  I have already tried a reinstall and just seem to be going round in circles now.

---

### Post by ~LoKe on 2007-12-14
Just chmod it again, but +x instead of -x.  

But the proper method would be to install sysv-rc-conf then do:
```
sudo sysv-rc-conf
```
Then go through the list and find the one called cupsys and disable id (move the arrow keys over the x's and press the spacebar).

---

### Post by 23meg on 2007-12-15
Is that really needed? Unchecking "Printer service" in System / Administration / Services seems to work.

---

