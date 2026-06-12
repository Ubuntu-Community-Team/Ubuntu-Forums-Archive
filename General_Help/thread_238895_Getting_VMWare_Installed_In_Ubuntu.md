---
title: "Getting VMWare Installed In Ubuntu"
date: 2006-08-18
forum: General Help
---

### Post by Mennisco on 2006-08-18
I've managed to successfully install VMWare in Suse 10.0 and 10.1, but I'm running into the same problem in Ubuntu as with Fedora - it wants to know the location of the C header files.  I think this means the c++ compiler may not be installed, though I'm not entirely sure if that's the problem.  

Can anyone tell me if I need to install extra packages [like gnu c++ compiler, kernel sources, make] and if so, where do I find them? - on the install DVD?  

Thanks!

---

### Post by rowanparker on 2006-08-20
Have you install build-essentials?
```
sudo apt-get install build-essential
```

---

