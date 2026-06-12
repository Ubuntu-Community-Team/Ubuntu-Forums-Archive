---
title: "Removing obsolete initrd.img files?"
date: 2021-08-01
forum: General Help
---

### Post by rsteinmetz70112 on 2021-08-01
I just upgraded from 18.04 to 20.04 and I noticed that there are two initrd.img files for kernels that are not longer installed.
```
initrd.img-4.4.0-103-generic  
initrd.img-4.4.0-112-generic 
```

Can these files simply be deleted?

---

### Post by Bashing-om on 2021-08-01
rsteinmetz70112 - well ///

Take a gander at what is installed:
```

dpkg -l | grep linux- 
ls -al /boot #(vmlinuz -> vmlinuz-5.4.0-80-generic) in my use case

```

What is the booting kernel:
```

uname -r

```

Then see if the system will remove those old .img files for you safely - if it is not related to the booted kernel [safety is no accident].
```

sudo apt update
sudo apt full-upgrade
sudo apt --purge autoremove

```

[INDENT]let the kernel do its thing
[/INDENT]

---

### Post by rsteinmetz70112 on 2021-08-02
```
#apt autoremove
``` cleaned thigs up.

---

### Post by Bashing-om on 2021-08-02
rsteinmetz70112; Yay :D

Pleased it wad as easy as pushing the button.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

