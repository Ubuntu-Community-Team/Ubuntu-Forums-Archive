---
title: "Compiz Fusion How-To?"
date: 2008-04-26
forum: General Help
---

### Post by Justin125 on 2008-04-26
Can someone redirect me to a compiz fusion installation how-to for Hardy 8.04? I've googled already but most of what I find is a bit old.

---

### Post by Zorael on 2008-04-26
If you're running Ubuntu (and not Kubuntu or Xubuntu), it should be installed by default. Just find Advanced Desktop Effects (or something along those lines) in the menus and try to enable stuff.

I'm not sure, but you may need to manually install the extra fusion plugins ("experimental") if you want those. Just open up Synaptic, search for **compiz-fusion** and toggle relevant results for installation.

Also, while not necessary, I suggest you also grab the **compizconfig-settings-manager** package, to get the real config app instead of the dumbed-down Advanced Desktop Effects one. You are, of course, free to choose which one to use, but the real one (ccsm in short) is superior in every way. It's more advanced and complicated, though.

---

### Post by Justin125 on 2008-04-26
> **Zorael said:**
> If you're running Ubuntu (and not Kubuntu or Xubuntu), it should be installed by default. Just find Advanced Desktop Effects (or something along those lines) in the menus and try to enable stuff.

I'm not sure, but you may need to manually install the extra fusion plugins ("experimental") if you want those. Just open up Synaptic, search for **compiz-fusion** and toggle relevant results for installation.

Also, while not necessary, I suggest you also grab the **compizconfig-settings-manager** package, to get the real config app instead of the dumbed-down Advanced Desktop Effects one. You are, of course, free to choose which one to use, but the real one (ccsm in short) is superior in every way. It's more advanced and complicated, though.

There isn't any 'Advanced Desktop Effects' anywhere in any menus, but I did DL the settings manager you mentioned but it's as if Compiz Fusion isn't install because anything I set in there doesn't seem to work.

Do you think it isn't installed? I'm running Hardy.

EDIT: Whoops, it is working!

---

### Post by the yawner on 2008-04-26
System>Preferences>Appearance

Go to Visual Effects tab and click Normal or Extra to enable Compiz Fusion.

---

### Post by Justin125 on 2008-04-26
> **the yawner said:**
> System>Preferences>Appearance

Go to Visual Effects tab and click Normal or Extra to enable Compiz Fusion.

Yeah, I did that and it works good now.

---

### Post by Zorael on 2008-04-26
Arr, that's what happens when you haven't run Gnome in a year. :>

---

### Post by Shadius on 2008-04-29
Can someone help me with Compiz Fusion please!? I'm dying here. Here's my story. I installed compiz-git, from a script I found in the forums, and I uninstalled the script because it was buggy, then I tried to get ccsm from the terminal and now I'm getting errors. I don't know how to fix it. Help pleaaaaaaaaaaaaaaaaaase.

---

### Post by Zorael on 2008-04-29
Can't promise you it'll work, but try this.
```
$ sudo aptitude purge ~ncompiz ~nemerald ~nlibdeco
$ sudo aptitude update
$ sudo aptitude install compiz compizconfig-settings-manager emerald
```

---

