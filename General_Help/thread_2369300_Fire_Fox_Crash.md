---
title: "Fire Fox Crash"
date: 2017-08-21
forum: General Help
---

### Post by jasemon on 2017-08-21
Hello - 

I would like instructions on how to download a replacement of Fire Fox because my current Fire Fox application does not load and crashes.  Perhaps after downloading it and reinstalling the software it will function again?  Thank you.

---

### Post by Autodave on 2017-08-21
Would like to know what version of Ubuntu you are running. You coul;d go into the Software Center and then navigate to Firefox. From there, remove it and then reinstall it.

---

### Post by ajgreeny on 2017-08-21
*Thread moved to **General Help**.* which is more appropriate and a better fit as this has nothing to do with your choice of desktop environment.

Try renaming the hidden **.mozilla** folder in your home to see if that solves the crashes; it is more likely to be the configuration of the application than the application itself.

---

### Post by jasemon on 2017-08-21
Is there a command line I can utilize in the Mate Terminal to download and overwrite Firefox?

---

### Post by VMC on 2017-08-21
Have you first tried renaming ".mozilla" in home dir?

---

### Post by timgood on 2017-08-21
> **jasemon said:**
> Is there a command line I can utilize in the Mate Terminal to download and overwrite Firefox?
```
sudo apt remove --purge firefox
```
```
sudo apt install firefox
```

---

### Post by jasemon on 2017-08-21
I decided to delete Firefox and use Chromium.  Thanks for all of your help.  All of you are appreciated!

---

