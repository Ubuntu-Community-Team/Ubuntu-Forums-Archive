---
title: "Accessing XP Registry from Ubuntu"
date: 2008-02-16
forum: General Help
---

### Post by Rohaq on 2008-02-16
I'd like to access the binary registry files from my XP partition through Ubuntu, in order to copy some values from there into wine without jumping back and forth between OSes. Does anyone know of a program that will let me decode the binary registry, or allow me to access the registry file and export .reg files?

Cheers!

---

### Post by chrisccoulson on 2008-02-16
I'm not sure if you can use wine to manipulate the registry? i think your choices will be very limited

This is the downside to binary configuration files (compared to human readable text files), I'm afraid.

---

### Post by 444 on 2008-02-16
Classic Regedit with Wine. Not the built-in regedit, you want the MS Regedit. The MS one can load the registry hives from C:\windows\system32\config.

There is also the command-line chntpw.

---

### Post by Rohaq on 2008-02-16
A little Googling reveals that there used to be a tool called dumphive that could turn the binary files into readable text reg files, but I can't find anywhere to obtain it, or how to use it :(

Anyone else used this and know where to get it?

---

### Post by Rohaq on 2008-02-16
> **444 said:**
> Classic Regedit with Wine. Not the built-in regedit, you want the MS Regedit. The MS one can load the registry hives from C:\windows\system32\config.

There is also the command-line chntpw.
I'll have a go at the CLI one, but the MS regedit.exe doesn't seem to want to run under Wine :(

---

### Post by 444 on 2008-02-16
Googling just "dumphive" helps too, even though the seems to have taken it down there are other sites with it.

---

