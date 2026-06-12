---
title: "Flash Failure  --  'dpkg --configure -a'"
date: 2006-12-08
forum: General Help
---

### Post by jhuff on 2006-12-08
I tried to install install flashplugin-nonfree and it locked.  Now I can not run any package management program.  I get an error that tells me  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  I try and run 'dpkg --configure -a' and it just locks up and does nothing.  How do I can I fix this mess. ](*,)](*,)](*,)](*,)](*,)

---

### Post by jhuff on 2006-12-08
I think I found the answer.  I found it on a Mepis Forum.  

```
sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree
```This seems to have freed up Synaptic so I can at least install other programs.  If anyone has any suggestions on how to install Flash Player I could really use the help.

---

### Post by taurus on 2006-12-08
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

