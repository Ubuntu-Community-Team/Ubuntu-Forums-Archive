---
title: "How to uninstall Adobe Flash"
date: 2008-06-08
forum: General Help
---

### Post by Jenga-kun on 2008-06-08
Yeah I have adobe flash installed and I tried to do this: [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

Now my flash isn't working and I think it's because I didn't uninstall adobe flash, problem is is that I don't even know how to uninstall it. Help please.

---

### Post by Jenga-kun on 2008-06-09
Can I get some help please?

---

### Post by PmDematagoda on 2008-06-09
Try:-
```
sudo apt-get remove --purge flashplugin-nonfree
```

---

### Post by Jenga-kun on 2008-06-09
> **PmDematagoda said:**
> Try:-
```
sudo apt-get remove --purge flashplugin-nonfree
```

Yeah I did that and this is what I got:
james@james-desktop:~$ sudo apt-get remove --purge flashplugin-nonfree
[sudo] password for james:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  nspluginwrapper libflac++6 kdebase-bin libdbus-qt-1-1c2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
james@james-desktop:~$

---

### Post by Jenga-kun on 2008-06-09
Come on there's gotta be someone here who can help me.

---

