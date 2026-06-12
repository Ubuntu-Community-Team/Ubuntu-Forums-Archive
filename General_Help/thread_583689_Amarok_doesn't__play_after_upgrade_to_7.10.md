---
title: "Amarok doesn't  play after upgrade to 7.10"
date: 2007-10-20
forum: General Help
---

### Post by geovino on 2007-10-20
After the upgrade to 7.10 Amarok doesn't open anymore. I uninstalled and reinstalled and it did nothing. 
This ia what I get at the terminal:

davek@davek-desktop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarokapp: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
davek@davek-desktop:~$ amarokapp
amarokapp: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
davek@davek-desktop:~$ 

How can I fix this?

---

### Post by por100pre1 on 2007-10-21
Try this:

```
sudo aptitude install libgl1-mesa-glx
```

if it is already installed:

```
sudo aptitude reinstall libgl1-mesa-glx
```

---

### Post by geovino on 2007-10-21
> **por100pre1 said:**
> Try this:

```
sudo aptitude install libgl1-mesa-glx
```

if it is already installed:

```
sudo aptitude reinstall libgl1-mesa-glx
```


Ran the first command and it ran it's install. But after that I click on Amarok and it just flashes the splash screen for a split second then disappears. So no Amarok yet. Any other clues? 

I'll reboot and see if that helps...  Nothing. Tried the second command and still nothing. What would cause something like this? 

The upgrade to Gutsy was a bit rocky, but the only things that don't work from what I can see is Amarok not working and not able to install Nvidia drivers and be able to use the desktop effects. 

In the future I'll back up important files and do a clean install... no more version upgrades!

---

