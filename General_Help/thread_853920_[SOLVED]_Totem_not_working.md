---
title: "[SOLVED] Totem not working"
date: 2008-07-09
forum: General Help
---

### Post by Darkade on 2008-07-09
Totem video player is not working. I dunno why... I tried installing xfce desktop and I failed. so I uninstalled it and everything is back to normal except for that. I can't use totem, nor can I play mp3, via gstreamer, I do have double checked if I have enabled restricted modules, and all that. When I run totem in a terminal I get this:
```
ivan@icarus-laptop:~$ totem
totem: error while loading shared libraries: libgstvideo-0.10.so.0: cannot open shared object file: No such file or directory
ivan@icarus-laptop:~$ 

```

but libgstvideo is not in the repos, and I mean if it's not in the repos, and it used to work fine then, Why is it asking for libgstvideo?

in case you ask this is what i get when I try to install libgstvideo

```
ivan@icarus-laptop:~$ sudo apt-get install libgstvideo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgstvideo

```

```
ivan@icarus-laptop:~$ sudo apt-get install libgstvideo-0.10.so.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgstvideo-0.10.so.0

```

Any ideas? thanks :D:D

---

### Post by kostkon on 2008-07-09
It must belong to one of the gstreamer plugins packages. For a start, try to reinstall the *libgstreamer0.10-0* and *libgstreamer-plugins-base0.10-0* packages.

---

### Post by Darkade on 2008-07-09
Thanks that worked perfectly. :D:D

---

