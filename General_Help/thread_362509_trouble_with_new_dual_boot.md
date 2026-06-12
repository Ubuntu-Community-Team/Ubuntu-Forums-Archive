---
title: "trouble with new dual boot"
date: 2007-02-15
forum: General Help
---

### Post by theacclaimed on 2007-02-15
Ok, so I departed on my own little adventure and I tried to dual boot my system with XP and ubuntu. Well I had a program called OS Selector from Acronis so I would be able to pick my OS at start up. Now after the install, it will always goto the linux partition, and the problem with that is that the OS Selector program was on the windows partition. So I need some program on Linux to do the same thing or I need a way to boot to my other partition. I've already tried installing some partition manager for Linux, but I had no idea even how to run the installation, so any suggestions? Help is greatly appreciated.

---

### Post by r4ik on 2007-02-15
Try,

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Good luck !

---

### Post by theacclaimed on 2007-02-15
i dont think anything is wrong with GRUB, it loads at boot and if i press exit the only things that show up are two versions of ubuntu and a memory test.

---

### Post by robcarr2 on 2007-02-15
Are you sure you haven't wiped your Windows partition and installed Linux over it by accident? Try putting in your Windows CD when booting up, it usually lets you boot straight into Windows, or alternatively if you go into the recovery console by using the Windows CD you should be able to choose from a list of current installations (C:\WINDOWS should be there for you)

---

### Post by r4ik on 2007-02-15
Try,

boot into the repair section of the install cd (xp). and type "fixmbr

Good luck !

---

### Post by theacclaimed on 2007-02-15
it is there. ok ill try that.

---

### Post by robcarr2 on 2007-02-15
Ye, if you desperately need to get back into Windows use the fixmbr command like r4ik suggested, works every time ;)

---

### Post by theacclaimed on 2007-02-16
fixmbr made it so that i was locked out of all my partitions.  i had to install a new one just to do anything.  thanks anyways.

---

