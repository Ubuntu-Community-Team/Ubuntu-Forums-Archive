---
title: "help with error"
date: 2008-04-05
forum: General Help
---

### Post by mr.farenheit on 2008-04-05
i recently re installed ubuntu 7.10. the only problem so far is that it shows no boot gui in the beginning. it doesn't show the loading bar or the check list at the beginning. i don't mine much but its knd of a reassurance to see that its acutally working and not just a blank screen.

---

### Post by reeseslover531 on 2008-04-05
what graphics card are you running?  If you are runnng some nvidia cards, it doesn't work and you just have to remove the splash item from the grub options.  This will show you the checklist.  That is how I did it and I have a 8800GT

---

### Post by mr.farenheit on 2008-04-05
ati radeon xpress 1100 chipset

---

### Post by reeseslover531 on 2008-04-05
i am not sure about the graphics card but it might help to remove the splash part of the grub kernel options.

---

### Post by mr.farenheit on 2008-04-05
how do i go about removing the splash item from grub?

---

### Post by lswest on 2008-04-05
```
gksudo gedit /boot/grub/menu.lst
``` and then find the entry for your linux partition (towards the end of the file) and then just delete "splash" from the line where you see it.

---

### Post by mr.farenheit on 2008-04-05
thank you much

---

### Post by mr.farenheit on 2008-04-05
it says splash in two places do i delete both?

---

### Post by tamoneya on 2008-04-05
They are for two separate boot sequences.  I would recommend only delete the one of the default boot sequence.  Leave the one on the recovery mode.  Just incase something goes wrong you dont want to have it affecting the recovery mode boot as well.

---

