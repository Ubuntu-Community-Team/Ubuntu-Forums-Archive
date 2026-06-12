---
title: "Desktop advance effects not showing up"
date: 2008-06-04
forum: General Help
---

### Post by qtmony14 on 2008-06-04
I'm using Ubuntu Feisty Fawn, and I finally got my nv17 geforce4 420 go 32M restricted video card to work, but I am still not able to change the desktop effects to normal or anything higher.  My advance desktop effects are not coming up in the system's options.  I have installed the compiz manager using the terminal, but still no advanced desktop effects. Sorry for the vagueness.. I'm a new user.. just installed today.  Any help would be greatly appreciated.  Thanks!:)

---

### Post by DesiDishoom on 2008-06-04
this happened to me as well. i was able to fix it by updating the available packages in Synaptic (System->Administration->Synaptic Package Manager, then click on "Reload"). Once the update is complete, you should be able to see the new nVidia drivers available for installation under System->Administration->Hardware Drivers. Then click the checkbox next to your card to install the new drivers.

let me know if this works! there are a few other things to check if this doesn't solve the problem or you get any errors in the process. good luck!

---

### Post by Forlong on 2008-06-04
Feisty is way too old, when you want to use Compiz.
How did you install Compiz Fusion on that install in the first place?
I guess through a third party repository. Those are not supported anymore.

If you just installed anyway, download a copy of Ubuntu 8.04 "Hardy Heron" and install that instead --it has Compiz Fusion installed by default and the settings manager is easily installable afterwards:
```
sudo apt-get install compizconfig-settings-manager
```

---

