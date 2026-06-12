---
title: "Having trouble in 17.04 installing GPA"
date: 2017-05-04
forum: General Help
---

### Post by swright198 on 2017-05-04
The Ubuntu installation post says to just update then install,.... It doesn't work
I tried downloading and compiling from scratch and it "builds" but won't "make"
I tried installing the GPA from .deb file.    The installer pops up but won't accept the OK to install when I click it.


I've tried updating and upgrading... but still get same results even after.

Memory 7.7GB
Processor: AMD A10-6800K APU with Radeon(tm) HD Graphics × 4 
Graphics: Gallium 0.4 on NV117
OS Type: 64-bit

---

### Post by Frogs Hair on 2017-05-04
Hello and Welcome ! 

If it's the following application use the repository version.

> The GNU Privacy Assistant (GPA) is a graphical user interface for the
GNU Privacy Guard (GnuPG).  It can be used to encrypt, decrypt, and sign
files, to verify signatures and to manage the private and public keys.


```
sudo apt install gpa
```

---

### Post by swright198 on 2017-05-04
Thank you.  I tried your suggestion and this is the error :

ubuntu@ubuntu:~$ sudo apt install gpa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gpa

---

### Post by Frogs Hair on 2017-05-04
Open software & updates and enable the Canonical Partners repository under other software and try again.

---

### Post by swright198 on 2017-05-04
Thank you.  I tried that ... I also ticked the all 4 boxes under "downloadable from the internet" on the main screen for Software and Updates.
main 
universe 
restricted
multiverse

between the 2 things I did, one fixed the problem.  Thank you for your kind assistance.   :)

---

### Post by Frogs Hair on 2017-05-04
Strange these were not enabled . You may want to run the software updater.

> main 
universe 
restricted
multiverse

---

