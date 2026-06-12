---
title: "grub parameters fo boot in CLI"
date: 2007-01-07
forum: General Help
---

### Post by Wofl on 2007-01-07
ok, i had a command line system set up, but then i needed a gui for a few things. so i installed kde on top of it. works all nice and so on, but i want to boot into the cli on default.

what kernel parameters are needed to deactivate the gui and just load the cli???
i can do the rest in grub

thanks

---

### Post by taurus on 2007-01-07
Just remove the kdm and it won't load.

```
sudo aptitude remove kdm
```

---

### Post by Ramses de Norre on 2007-01-07
Or remove the symlink for kdm from /etc/rc2.d/.

---

### Post by Wofl on 2007-01-07
well i wanted to have the old boot parameter in order to boot nto kde from time to time, bot the default boot option to load it without...

i just dont want it to load it on default

---

### Post by llamakc on 2007-01-07
Do you mean you want the login-manager to load on occasion? You can start KDE from the commandline: it doesn't have to be loaded after shutting the machine down/up.

---

### Post by Wofl on 2007-01-07
well i am looking for a way of having the possibility to boot into kde from rime to time, but normaly i want to boot into the command line.

the possbility i thought of was having the entries in the grub menu
one for cli (default)
one for kde
then failsave and memtest


any other option sounds good too
just tell me what to do

---

### Post by llamakc on 2007-01-07
You don't need to worry about it at "boot time" inside of GRUB. If you already have your machine setup so that it boots to the command prompt, just have a user create a ~/.xinitrc file that has this as its contents:

exec startkde

and then as USER, you would type "startx" on the commandline. This way bypasses using a login-manager (KDM, GDM).

Does that help? I believe startx is in the package 'xbase-clients'.

---

### Post by Ramses de Norre on 2007-01-07
Or download sysv-rc-conf, run it with sudo and turn kdm on in one runlevel and off in another one. Then make two grub entries for this runlevels (By default grub boots to two).
Untill dapper it was possible to just append the number of the runlevel to the end of the kernel line but that seems to have changed in edgy. I don't know the exact option to do it now but it should exist.

---

### Post by Absorto on 2007-04-15
I run edgy. I setup a custom kernel for which I want my system to boot on runlevel 3 instead of runlevel 2. I appended a "3" to the kernel line in grub, but it doesn't work, it boots to runlevel 2 all the same.

---

### Post by Ramses de Norre on 2007-04-16
That's a known bug... I don't know a solution though.

---

