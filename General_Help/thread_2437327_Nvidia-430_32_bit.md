---
title: "Nvidia-430 32 bit"
date: 2020-02-21
forum: General Help
---

### Post by monkeybrain20122 on 2020-02-21
I recently upgraded my Nvidia driver from 418 to 430 on Ubuntu 16.04 and found that 32 bit support is missing so many wine apps stop working.

```
 ldconfig -p | grep libGL.so
 libGL.so.1 (libc6,x86-64) => /usr/lib/nvidia-430/libGL.so.1
  libGL.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libGL.so
 libGL.so (libc6,x86-64) => /usr/lib/nvidia-430/libGL.so


```

With Nvidia-418
```

ldconfig -p | grep libGL.so
 libGL.so.1 (libc6,x86-64) => /usr/lib/nvidia-418/libGL.so.1
  libGL.so.1 (libc6) => /usr/lib32/nvidia-418/libGL.so.1
 libGL.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libGL.so
 libGL.so (libc6,x86-64) => /usr/lib/nvidia-418/libGL.so
 libGL.so (libc6) => /usr/lib32/nvidia-418/libGL.so


```

I checked that the directory /usr/lib32/nvidia-430 did exist and was populated (and libGL.so was in there) but somehow it wasn't picked up.

I am wondering if others may be running higher versions of Ubuntu experience the same issue.

I made a bug report[ here ]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-430/+bug/1863992")

---

### Post by Holger_Gehrke on 2020-02-21
Check the configuration of the library loader cache in /etc/ld.so.conf (and the files in /etc/ld.so.conf.d/ which will get included by /etc/ld.so.conf as it's set up on Ubuntu by default). '/usr/lib32' is not a standard directory on Ubuntu, the standard place for 32-bit libraries AFAIK is '/usr/lib/i386-linux-gnu' and/or '/lib/i386-linux-gnu'. You might have to add a *.conf in /etc/ld.so.conf.d/ and run ldconfig to add the libraries in those directories to the cache.

Holger

---

### Post by monkeybrain20122 on 2020-02-21
@Holger_Gehrke

But it works for Nvidia-418.

---

### Post by monkeybrain20122 on 2020-02-23
Hi moderator the tag of this should be ubuntu instead of lubuntu. Please help me change it, thanks.

---

### Post by wildmanne39 on 2020-02-23
Done! please use the report button in the future.

---

### Post by mc4man on 2020-02-23
If you've no response to bug then maybe use launchpad mail on that ppa, they've responded to me in past reasonably soon.

16.04 still uses update-alternatives, seem that the 2 i386 ones are linked to the 64bit libs.. When installing 430 it would have printed out in terminal what was being done as far as alternatives and their links..
(- 18.04+ no longer uses alternatives, it installs a ton of packages for both amd64 & i386

After the fact, short version can be seen via
```

update-alternatives --list i386-linux-gnu_gl_conf

update-alternatives --list  i386-linux-gnu_egl_conf
```

Longer via this shows more info & links  
```
 update-alternatives --display i386-linux-gnu_gl_conf

update-alternatives --display i386-linux-gnu_egl_conf
```

just plain  update-alternatives --all  - 
```
There are 3 choices for the alternative i386-linux-gnu_gl_conf (providing /etc/ld.so.conf.d/i386-linux-gnu_GL.conf).

  Selection    Path                                         Priority   Status
------------------------------------------------------------
* 0            /usr/lib/nvidia-430/alt-ld.so.conf            8604      auto mode
  1            /usr/lib/i386-linux-gnu/mesa/ld.so.conf       500       manual mode
  2            /usr/lib/nvidia-430-prime/alt-ld.so.conf-pm   8603      manual mode
  3            /usr/lib/nvidia-430/alt-ld.so.conf            8604      manual mode
```
```
There are 3 choices for the alternative i386-linux-gnu_egl_conf (providing /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf).

  Selection    Path                                         Priority   Status
------------------------------------------------------------
* 0            /usr/lib/nvidia-430/alt-ld.so.conf            8604      auto mode
  1            /usr/lib/i386-linux-gnu/mesa-egl/ld.so.conf   500       manual mode
  2            /usr/lib/nvidia-430-prime/alt-ld.so.conf-pm   8603      manual mode
  3            /usr/lib/nvidia-430/alt-ld.so.conf            8604      manual mode

```

---

