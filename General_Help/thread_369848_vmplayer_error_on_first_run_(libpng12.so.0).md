---
title: "vmplayer error on first run (libpng12.so.0)"
date: 2007-02-25
forum: General Help
---

### Post by seshomaru samma on 2007-02-25
I installed the latest vmplayer from vmware website
the installation was smooth but when i run it i get:
```

/usr/lib/vmware/bin/vmplayer: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
```

---

### Post by taux on 2007-02-25
You should do this:

```

sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/

```

If vmware still does not work try this:

```

LD_PRELOAD=/usr/lib/libdbus-1.so.3:$LD_PRELOAD vmware

```

---

### Post by seshomaru samma on 2007-02-25
thanks but now i don't get any errors , vmplayer simply doesn't run....

---

### Post by taux on 2007-02-25
Did you try this command?

```
LD_PRELOAD=/usr/lib/libdbus-1.so.3:$LD_PRELOAD vmware
```

---

### Post by seshomaru samma on 2007-02-25
yep

```
ERROR: ld.so: object '/usr/lib/libdbus-1.so.3' from LD_PRELOAD cannot be preload
```

I guess the gods dont want me to run XP on a virtual machine
I tried vmserver , vmplayer , virtualbox...all failed....

---

