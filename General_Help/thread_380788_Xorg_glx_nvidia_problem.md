---
title: "Xorg glx nvidia problem"
date: 2007-03-10
forum: General Help
---

### Post by MikaelHolber on 2007-03-10
Hi,

I'm having problem with the libglx.so module and I think I know what is wrong but don't know how to fix it.

Starting X gives this 
```
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
dlopen: /usr/lib/libGLcore.so.1: undefined symbol: _nv000043gl
(EE) Failed to load /usr/lib/xorg/modules//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)

```

As you might notice there is a double slash in the path. I don't know how it got there and don't know how to fix it. The X-server starts without glx but no eye-candy can live without it. I'm am running Feisty in order to get support for the hardware in my new laptop. The laptop is a HP dv2000 intelbased.

Thank you for your help.

---

### Post by ShiftyPowers on 2007-03-10
crap, ihave the same issue and don't know how to figure out the solution

---

### Post by MikaelHolber on 2007-03-11
I have found the answer. I previously installed the binary from Nvidias homepage (newer version). Make sure to remove all libGLcore.so and libGL.so files that belongs to the newer version (search for them with "locate 9755" if the binary version is 9755). Redirect the symlinks to the original nvidia-glx (newest in feisty is 9631). 
```
ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so.1.0.9631
```
and so on. Works like a charm.

---

### Post by nicjasno on 2007-03-12
Sorry to hijack your thread, but i have another Nvidia glx related problem.

I noticed this, because i am running beryl. I installed fresh nvidia drivers, and glxinfo saig that direct rendering was enabled. Also nvidia-settings showed all the info.

But after the next boot, direct rendering didn't work. And beryl was unable to start.

I then disabled the glx module in xorg and rebooted x. It failed to load, of course. Then i enabled the glx module again, and direct rendering worked again.

What can i do, to fix this? I have run out of ideas.

---

