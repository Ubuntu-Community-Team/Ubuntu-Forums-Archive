---
title: "can't dpkg --purge my nvidia driver"
date: 2008-04-30
forum: General Help
---

### Post by MonkeyPlus on 2008-04-30
I try and I get the following: 

```
Removing nvidia-glx ...
dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx (--purge):
 subprocess post-removal script returned error exit status 2

```

Tried it through synaptic as well, with the same result (I presume because it is doing the exact same thing). 

I'm running 64-bit hardy, on an Athlon 3200+ with a Geforce 7100GS graphics card.

---

### Post by kpkeerthi on 2008-04-30
Can you post the output of ```
ls -l /usr/lib32/libGL.so.*
```?

---

### Post by MonkeyPlus on 2008-04-30
```
ls: cannot access /usr/lib32/libGL.so.*: No such file or directory

```

I installed nvidia-glx directly from synaptic, and then tried to enable it with the 'Hardware Drivers' programme. Now everything has gone balls up. I can't install any other packages it seems whilst this process won't run.

---

### Post by ryanhaigh on 2008-04-30
Looks like its trying to remove a file that apparently has already been removed through some other process. You could try to create a dummy file of the same name and allow it to remove that. Not sure if this is recommended but it may get you out of trouble.
```

sudo touch /usr/lib32/libGL.so.1

```

---

### Post by MonkeyPlus on 2008-04-30
From the above its quickly become aparant that /usr/lib32 does not exist. In retrospect this isn't exactly surprising on a 64-bit system.

I think what has happened is that when i installed nvidia-glx it tried to create a file in a folder that doesn't exist, and now is trying to delete it and failing.

I'm going to try and create a lib32 folder just for the purpose of removing this package.

Seems that I am not the first with this particular problem: 
[http://ubuntuforums.org/showthread.php?t=770097&highlight=nvidia-glx](http://ubuntuforums.org/showthread.php?t=770097&highlight=nvidia-glx)

---

