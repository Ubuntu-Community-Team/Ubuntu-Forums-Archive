---
title: "Wine 0.9.31 crash"
date: 2007-02-18
forum: General Help
---

### Post by voided3 on 2007-02-18
Hello, I just installed wine using automatix2 and the installation was successful, but when i run "winecfg" in the terminal either as a user or root, it freezes the computer when it is "creating configuration directory" in my home folder. Any thoughts? Thanks!

---

### Post by voided3 on 2007-02-28
Oh, I forgot to mention that it does create a C:\WINDOWS directory in the .wine folder, but I am still puzzled. Any other ideas?

---

### Post by AlcoJaguar on 2007-02-28
You shouldn't be creating a .wine directory for the root user, at least in my limited experience with wine. remove .wine from your user's home folder and use winecfg again. Let it run, it does take a moment to create the directory and set up the default registry and such.
 
Ed:
Also what version of Wine are you using and what repository did you get it from?

---

### Post by voided3 on 2007-02-28
Hey, it creates a .wine folder for my user home folder. I logged in as root and didn't see a .wine folder there.

---

### Post by Shay Stephens on 2007-02-28
Why are you using root?  You don't need to be root to use wine.  Log in as a user and use it that way.  Does it still crash?

---

### Post by gosh on 2007-06-19
I have  exactly the same problem.
Installed wine 0.9.39 from wine.budgetdedicated.com/apt feisty main
Then ran winecfg from a terminal and my computer freezes.
I did create a .wine dir with /dosdevices and /drive_c/windows but no /drive_c/Program \Files.

anyone>

---

### Post by Shay Stephens on 2007-06-19
you shouldn't have to manually create those folder, they should be made when winecfg runs if they do not already exist.  I would delete the .wine folder and try running winecfg again.  If you still have the problem, uninstall, delete the .wine folder, redownload wine and start fresh.  Maybe the original download was corrupt or the wrong version or something.

---

### Post by Qu4k3R on 2007-06-19
Try this repo:
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

It's the one I use, and It is working for now (updated).

---

### Post by gosh on 2007-06-20
> **Qu4k3R said:**
> Try this repo:
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

It's the one I use, and It is working for now (updated).
No luck. I purged wine and installed it through this repo, but still the same. Winecfg freezes my system after creating .wine

---

