---
title: "No &quot;edit as root&quot; in KDE4 remix's Dolphin"
date: 2008-04-26
forum: General Help
---

### Post by chjornaq on 2008-04-26
So one of my favorite things about Kubuntu Gutsy was the "Edit/Open As Root" action menu item that also popped up on the right sidebar of Dolphin, but I'm using a multi-boot setup with the Kubuntu KDE4 remix as one of the distros I'm booting to and there's nothing similar.
 
I discovered this when I needed to change up my fstab and couldn't find an Edit as Root button, so I went to terminal and typed in "sudo kate /etc/fstab" and after password it gave me 
```
sudo: kate: command not found
``` 
so I plugged in a "which kate" and it said
```
/usr/lib/kde4/bin//kate
```
 
I tried 
```
sudo /usr/lib/kde4/bin//kate /etc/fstab
```
and that worked fine, but that double-slash doesn't seem right, but everything in the kde4/bin directory 'which'es this way.
 
So my question is a two-parter: 
1) does that goofy path have anything to do with my lack of a convenient "edit as root" sidebar (and would I just have to change the PATH env variable)
and 
2) I know that in the repositories nautilus has nautilus-actions to allow for easy setup of an action menu, including root actions, so do I just need to find something similar for Dolphin?

---

