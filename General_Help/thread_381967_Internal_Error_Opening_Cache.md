---
title: "Internal Error Opening Cache"
date: 2007-03-11
forum: General Help
---

### Post by Concorde on 2007-03-11
Ok, I was installing VirtualBox and when I did through terminal it did not install. (Wouldn't get past the PEUL stage) I thought I had all of the files needed to install VB.  Now I get this error message when I open up Synaptic:

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I can't install anything from Synaptic, any ideas what I can do to fix this

To me it seems like it is still waiting for the system to install VirtualBox. I installed the lib6-c files for VB and thought I had all of the files required.

Thanks for your help

Concorde

---

### Post by dexter on 2007-03-11
Does it show up as installed under Synaptic ? If so, try uninstalling it. 

If it doesn't work through Synaptic, you can try removing it using apt-get:
```
sudo apt-get remove virtualbox
```

---

