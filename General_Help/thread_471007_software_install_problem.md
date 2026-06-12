---
title: "software install problem"
date: 2007-06-11
forum: General Help
---

### Post by edq on 2007-06-11
Hello,

I recently tried to install  the virtualbox program on my computer and ran into some problems. The installation seemed to stall and I killed the installer using xkill. I would like to try to uninstall or reinstall the program. However, synaptic will not run because:

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

and the virtualbox package installer will not open.  How should I fix this problem?

---

### Post by LollYouSuckZor on 2007-06-11
```


sudo apt-get remove virtualbox virtualbox-plugins


```

Im not sure if that's right, it depends on what the packages names are.  Just replace virtualbox, and virtualbox-plugins, with the names of the packages.  
If you need to add more.  Just add them on like so..
```


sudo apt-get remove virtualbox virtualbox-plugins virtualbox-manager virtualbox-CookiesandCake


```

Hope that helps :) If not... post again and I'll have a look.

---

### Post by edq on 2007-06-11
Thanks for the suggestion. I tried your suggestion and this was the output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
 

Do I need to move the virtualbox installer to a specific folder so it can be "found"? RIght now the installer is on my desktop.

---

### Post by onero on 2007-06-13
Just so you know, Virtualbox has a repository for feisty ... just add "deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) feisty non-free" to your /etc/apt/sources.list file. You can do this via Synaptic as well. Then just try to install the virtualbox package that's in the repository. :)

---

### Post by edq on 2007-06-17
Onero,

This seems to have fixed the problem; thanks for your help!

---

