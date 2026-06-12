---
title: "error when I start synaptic"
date: 2006-10-24
forum: General Help
---

### Post by leveliv on 2006-10-24
here is what I get in a dialogue box when Synaptic opens:
```
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
 
```

anyone know what that is? and how I can fix it?

---

### Post by ~LoKe on 2006-10-24
Open up your terminal, and type the following:
```
sudo gedit /etc/apt/sources.list
```

Put ## in front of the top two lines (the ones that have "cdrom" in them).

---

### Post by leveliv on 2006-10-24
Thank You

---

### Post by ~LoKe on 2006-10-24
Not a problem.

---

