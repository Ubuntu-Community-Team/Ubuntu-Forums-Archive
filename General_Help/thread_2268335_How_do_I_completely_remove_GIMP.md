---
title: "How do I completely remove GIMP?"
date: 2015-03-08
forum: General Help
---

### Post by KayeNg on 2015-03-08
I installed GIMP, which took about 80+ MB to install.  Now I'm trying to uninstall it, and Software Center says only 15MB of space would be freed.  I want the remaining 70+ MB freed as well.  How do I do that? 
In other words, if it took 80MB to install, I want to have that 80MB back when I uninstall.

Thanks!

---

### Post by v3.xx on 2015-03-08
```
sudo apt-get autoremove
```
[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

There is also deborphan.

---

