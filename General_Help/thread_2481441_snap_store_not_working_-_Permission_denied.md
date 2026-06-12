---
title: "snap store not working - Permission denied"
date: 2022-11-29
forum: General Help
---

### Post by thephantom1972 on 2022-11-29
Hi,  

I have Ubuntu version 22.04 LTS, 64 bits, Gnome 42.5 with X11 (arm64). I don't see the Software Center. Is there an way to get it? 

i tried this steps but it did not work:

sudo apt update && sudo apt upgrade
sudo snap install snap-store

it gives me:

> error: cannot perform the following tasks:
- Run configure hook of "snap-store" snap if present (run hook "configure": cannot perform operation: mount --bind /snap/core20/current/etc/nsswitch.conf /tmp/snap.rootfs_pOsQ1F/etc/nsswitch.conf: Permission denied)

Someone an idee how to get this working?

---

### Post by QIII on 2022-11-29
Moved from chat area to General Help.

---

### Post by exploder on 2022-11-30
The snap store breaks every single time they update it, I have fixed it 3 times already! Here is the command I used to fix it.

```
sudo pkill snap-store && sudo snap refresh snap-store
```

Edit: I am not on the same platform but it's still worth a try.

---

### Post by thephantom1972 on 2022-11-30
Thnx, does not gives an error but also no snap store.

---

### Post by ian-weisser on 2022-11-30
Is your /home, by chance, symlinked from a different location or mounted from an external device? Those are classic causes of permission failures in nsswitch.conf.

---

### Post by thephantom1972 on 2022-12-05
no extarnal drive

---

