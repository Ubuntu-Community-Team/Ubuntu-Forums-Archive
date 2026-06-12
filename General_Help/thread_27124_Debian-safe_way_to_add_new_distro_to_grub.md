---
title: "Debian-safe way to add new distro to grub?"
date: 2005-04-14
forum: General Help
---

### Post by bawbag on 2005-04-14
Is there a tool for Debian based distros that would allow me to add an entry to Grub cleanly, without messing up apt's ability to upgrade kernels etc?

---

### Post by wfx on 2005-04-15
Hmm maybe im wrong (it is not realy clean for me what you want)

If you want or need any extra option for your kernel then add it like this:
```
...
....
# kopt=hdc=ide-scsi hdd=ide-scsi
...

``` 
The "#" is important and the option in this example is "hdc=ide-scsi hdd=ide-scsi".
This add everytime to all kernel checked by debians automatic this options.

if you want to add something what skip the debian automatic then under this:
```
...
### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

