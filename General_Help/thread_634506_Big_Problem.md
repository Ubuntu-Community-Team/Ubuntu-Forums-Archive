---
title: "Big Problem"
date: 2007-12-07
forum: General Help
---

### Post by panaretos22 on 2007-12-07
I have a problem when i am going to update.
Software index is broken

I[B][COLOR="Red"]t is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
i run the command into terminal and this is what i get :
The following extra packages will be installed:
  patch
Suggested packages:
  diff-doc
The following NEW packages will be installed:
  patch
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0B/95.6kB of archives.
After unpacking 193kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter[/COLOR][/B]
is anybody willing to help???

---

### Post by taurus on 2007-12-07
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

p.s.  So, did you insert the installer CD into the drive and hit Return?

---

### Post by panaretos22 on 2007-12-13
i have fix the problem....the problem it was in softawre sources the cd was ticked ...i have done the commands you gave me and works(thanx to the channel that help me)

---

