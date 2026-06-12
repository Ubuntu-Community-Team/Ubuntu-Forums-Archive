---
title: "How to uninstall a free trial version of Crossover"
date: 2013-05-29
forum: General Help
---

### Post by SuperFreak on 2013-05-29
I am trying to uninstall a free trial version of Crossover. I tried the uninstall icon in my main menu, no luck. I also tried sudo /opt/cxoffice/bin/cxuninstall but crossover still appears to be active in my main menu. I also tried searching for the package in synaptic with no luck. When I try uninstalling the first two ways I get a popup or message in terminal saying it is unistalled but crossover still appears in menu and opens when I click on it

---

### Post by Frogs Hair on 2013-05-29
If you have not logged out since removing the application try that first. Another thing to try would be open the home folder and use Ctrl + H to show hidden folders. Check for and remove the configuration it may have a title like .crossover. If you don't see any thing obvious check in the .config folder. If you are able to find and remove the folder log out and in or restart and see if the menu entry disappears.

---

### Post by SuperFreak on 2013-05-29
Thanks but I removed .crossover in home folder and logged out. Crossover is still there in menu and it still opens program

EDIT: There was another folder .cxoffice which I have also deleted. After logout it still seems to function and cxoffice just replaces itself.

Insidious

---

### Post by Frogs Hair on 2013-05-29
You could try autoremove since you have removed a number of dependencies already.

```
sudo apt-get autoremove
```

---

### Post by SuperFreak on 2013-05-29
> **Frogs Hair said:**
> You could try autoremove since you have removed a number of dependencies already.

```
sudo apt-get autoremove
```

Thanks but I don't think it worked

```
david@MainSqueeze:~$ sudo apt-get autoremove
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
david@MainSqueeze:~$ 

```

Not sure if this is important, but if I open Crossover it has this error message
 Missing 32bit libnss_mdns.so.2 library: This library is needed for network and Internet access. Installing it is strongly recommended.

---

### Post by Frogs Hair on 2013-05-29
Since it was a trial It might have left something hard to remove on your system to be sure that each user gets one free trial only.

---

### Post by SuperFreak on 2013-05-29
Hopefully once the trial ends it will uninstall...Thanks for your help

---

