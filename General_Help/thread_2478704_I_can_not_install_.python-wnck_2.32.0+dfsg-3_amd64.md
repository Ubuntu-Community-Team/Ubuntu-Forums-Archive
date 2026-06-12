---
title: "I can not install ./python-wnck_2.32.0+dfsg-3_amd64.deb"
date: 2022-09-02
forum: General Help
---

### Post by raleigh3 on 2022-09-02
I am trying to install this, but have errors. This is on Ubuntu Mate 20.04.

andy@7_~/Downloads$ sudo apt install ./python-wnck_2.32.0+dfsg-3_amd64.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'python-wnck' instead of './python-wnck_2.32.0+dfsg-3_amd64.deb'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 python-wnck : Depends: python-gtk2 but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by deadflowr on 2022-09-02
What release? Still 18.04 as stated in your signature or something else?

---

### Post by raleigh3 on 2022-09-02
20.04

---

### Post by raleigh3 on 2022-09-03
```
gdevilspie relies on PyGTK2, and with the removal of most Python 2 packages in current distributions, old gdevilspie packages are no longer installable.

It may be possible to install your package if you find packages for the dependencies (e.g. on snapshot.debian.org), if there are no conflicts with current Python packages on your system.

devilspie itself is still available, and installable directly in your distribution (e.g. sudo apt install devilspie). You can thus still write rules and have them applied to windows; you just won&#8217;t have the GUI provided by gdevilspie.
```

I copied the devilspie rules from my 18.04 to 20.04. Now my terminal windows start minimized.

---

