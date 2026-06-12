---
title: "Need help reinstalling missing library file(s)"
date: 2008-04-07
forum: General Help
---

### Post by Binary Dragon on 2008-04-07
I have no idea how this problem happened, but I need help in fixing it.  Upon trying to run vncviewer, I get the following error...

```
vncviewer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

Best I can figure, I'm just flat out missing that library file, but I can't figure out how to reinstall it.

A google search for the error message returned the solution of 
```
sudo apt-get install libstdc++2.10-glibc2.2
```
however an attempt to do that merely returns
```
E: Couldn't find package libstdc++2.10-glibc2.2
```

I'm currently using the latest updated version of the 8.04 Beta.  Please let me know if you have any ideas on how I can fix this.  Keep in mind that I am still pretty new to Linux, so I will likely need exact terminal commands to follow.  Thanks.

---

### Post by Het Irv on 2008-04-07
Have you tried searching Synaptic for "libstdc" or "libstdc++2.10-glibc2.2"?

I have seen where programs do not recognize updated versions of a library, and that may be your problem.

---

### Post by lfjewett on 2008-04-30
I to need this file but can't seem to find it.. Have multiverse enabled. apt-file search doesn't turn up any results :(  anybody got a solution to this?

---

