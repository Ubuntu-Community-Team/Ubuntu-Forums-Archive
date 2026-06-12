---
title: "Is there a list of commands to repair broken system components?"
date: 2020-10-29
forum: General Help
---

### Post by sofasurfer on 2020-10-29
For instance, when my desktop is not operating properly I can open terminal and run "sudo apt-get install ubuntu-desktop". The reinstalls the desktop. Now what is my file browser is dysfunctional, or is "copy and paste" is not working, etc, etc. 
Is there a list of commands to repair all the various functions that can break, so I do not need to reinstall the whole system if something is not working properly.

---

### Post by Impavidus on 2020-10-29
No.

**sudo apt-get install ubuntu-desktop** doesn't reinstall your desktop. It makes sure that the ubuntu-desktop package is installed. If it is (even if broken), it does nothing more. Else it will install ubuntu-desktop and all its dependencies (if missing). When your desktop is broken, it's because one of the dependencies of ubuntu-desktop is missing (installing ubuntu-desktop may fix it), broken (a reinstall of that package may fix it) or because there's something wrong with the configuration of the user (a new user will fix it). There are occasionally cases where something can be fixed by restarting some component.

When something is broken, you have to find out why, then fix it. A dumb one-fix-for-all command would be very useful, but if it magically existed, the devs would put it in a shell script and run it automatically every day so that every problem is fixed automatically in a day and there would be no need for the Ubuntu forums.

---

### Post by sofasurfer on 2020-10-29
Well then, should my question be...How do you tell which dependencies are broken/missing when you have a malfunction?

---

### Post by Frogs Hair on 2020-10-29
If there are problems with the package system you will see them in the the output of the following. ```
sudo apt update
``` There may also suggestions to fix broken packages in the output.

---

### Post by Impavidus on 2020-10-29
It requires the kind of detective work you get good at if you hang around enough at these forums. One trick: if you know a filename that's involved, dpkg can tell you the package name:```
dpkg --search filename
```

---

