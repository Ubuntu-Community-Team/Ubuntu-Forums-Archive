---
title: "Sweet Home 3D: cannot uninstall"
date: 2019-04-25
forum: General Help
---

### Post by lpalazzotto on 2019-04-25
I must have messed up with some of the dependencies of the package and now it does not work and I cannot completely uninstall it from my PC . Error: - 

[I]Unable to remove "Sweet Home 3D": 
E: Could not get lock /var/lib/dpkg/lock-frontend - open 
(11: Resource temporarily unavialable)
[/I]
I did use Synaptic to completely remove the program, and it seemed all ok, except that when I open Ubuntu Software the package is still there.

Not only I cannot uninstall it completely, but when I try to reinstall it from Synaptic it all looks fine, except that the program itself does not work when I try to launch it.

I have Ubuntu 19.04, but had the same problem with the 18.04. I was hoping the upgrade would have solved it, but the upgrade was itself complicated by an error (legacies that could not be found).

Anyone that has any idea about how to deal with this without resetting and reinstalling the whole Ubuntu?

---

### Post by cruzer001 on 2019-04-26
The sweethome3d site has instructions for removal, seems it does not remove cleanly.

So try this (one line at a time) while you have it installed:
```
sudo apt purge sweethome3d
sudo apt autoremove
sudo apt autoclean
```
Then open up your file manager and do a system (entire drive) search for *sweethome* and remove any left over crud.

---

### Post by lpalazzotto on 2019-04-26
It cleaned up everything: thanks!
You made it quite easy...

---

### Post by cruzer001 on 2019-04-26
Your welcome :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

