---
title: "Xorg + ATI + kernel + module DRIVING ME MAD!"
date: 2005-04-01
forum: General Help
---

### Post by sapo on 2005-04-01
Ok.. i ve managed how to put my 9800pro to work with the XFree86 server... dont ask me how i did it  :-? 

btw...

I ve update to xorg and now i cant compile the fuking kernel module... take a look:

root@xgn:/lib/modules/fglrx/build_mod # sh make.sh
ATI module generator V 2.0
==========================
initializing...
Error:
kernel includes at /usr/src/linux/include do not match current kernel.
they are versioned as "2.6.8"
instead of "2.6.8.1-5-386".
you might need to adjust your symlinks:
- /usr/include
- /usr/src/linux


I ve already changed the symlink of /usr/src/linux to /usr/src/linux-2.6.8.1-5-386

But how the hell am i going to change the includes? the include is a directory isnt it?

How can i sold it to install the module?  ](*,)

---

### Post by Dracontopes on 2005-04-01
Did you install the linux-headers?

---

### Post by sapo on 2005-04-01
[QUOTE=Dracontopes]Did you install the linux-headers?[/QUOTE]

Yes the problem was with the symlinks.. i fixed and compiled the fuking module.. but it still doesnt work!

So i downgraded to XFee86 and stopped burning my neurons  [-X

---

### Post by MadMan2k on 2005-04-02
why didnt you simply use the precompiled modules from the reprository?

---

### Post by bobmitch on 2005-04-02
[QUOTE=MadMan2k]why didnt you simply use the precompiled modules from the reprository?[/QUOTE]

Because they are an older version and problematic in the extreme.  These new drivers solve many many problems.
If only the old drivers were somehow a security risk, they may have included the newer ones in hoary... ;)

---

### Post by sapo on 2005-04-02
[QUOTE=MadMan2k]why didnt you simply use the precompiled modules from the reprository?[/QUOTE]


Is there a precompiled driver for xorg in the repository???

When i downloaded Xorg it just had the driver for XFree86 and i had to download de ATI driver...

---

### Post by sapo on 2005-04-02
i ve found the "pre-compiled module"

But when i try to load it with my kernel it says:

```

root@xgn:/home/sapo # modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.8.1-5-386/kernel/drivers/char/drm/fglrx.ko): Invalid module format
root@xgn:/home/sapo #

```

---

### Post by MadMan2k on 2005-04-03
you also have to load the kernel-modules-retricted or something - simply search for "fglrx" and you'll find it.

---

