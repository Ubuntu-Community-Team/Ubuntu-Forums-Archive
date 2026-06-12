---
title: "I really messed up!!!!"
date: 2007-02-04
forum: General Help
---

### Post by annex_225 on 2007-02-04
Ready??? 

New to Linux/ubunto                            "Yes" 
Dangerous with a Keyboard               "Yes"
Good at fallowing Instructions           " Sometimes"

Ok, It all started off with "Beryl",  will then after reboot and the Xserver wouldn't start...  Wrong Drivers for Video Card, I needed an older driver 96xx (Got it) "Nvidia G3 TI200 64MB". :idea: to make matters worse I removed the Xorg.conf File. However now i could get to my desktop :)  Now I want to create a new Conf file and install the new driver. :idea: I figured if I could install the correct driver the file would be created for me. however I can't install the file while Xserver is running and the driver   "warns" :confused: that i shouldn't install while in run level 1. so could someone pls give me some dirrection? I need kill the Xserver....  I think?

Thank

---

### Post by taurus on 2007-02-04
If you want to kill X, then just kill gdm.  That should stop X from running.  You can look up the PID for gdm from the output of this command, first column.  Make sure you log in from a console, <Ctrl><Alt>F2.

```
ps -A
sudo kill -9 **PID**
```

---

### Post by dozier768 on 2007-02-04
from root or su just run:  killall gdm , of course im assuming you've logged out of ubuntu and hit ctrl+alt+F1.

---

### Post by annex_225 on 2007-02-04
Thanks....  Got a little farther...  killed gmd and xorg...  tryed running the script that will install the driver i get "No Precompiled kernel interface was found to match my kernel. :confused:   the script tryed to download...  but none matched...  it is also unable to fine the kernel source tree for the currently running kernel...  I checked and installed kernel source that matched my CPU and also installed Kernel Packages as well as the Nvidia-legacy Kernel source....   Not sure what to do next...   Thanks Again](*,)

---

### Post by taurus on 2007-02-04
Here's something for you to look at.  It has both legacy and beta drivers.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by ~LoKe on 2007-02-04
Rather than outright kill GDM, I would just..
```
sudo /etc/init.d/gdm stop
```

---

