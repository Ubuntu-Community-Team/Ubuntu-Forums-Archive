---
title: "kernel 4.13 in ubuntu 17.10 generate issue in fstab and mounted folders"
date: 2017-10-21
forum: General Help
---

### Post by alain.roger on 2017-10-21
Hi,

i upgraded my kubuntu 17.04 to 17.10 so my kernel has been upgrade from 4.11 to 4.13.
With such upgrade came issues related to kernel 4.13 and i would like to understand in order to fix them.

1. in /mnt folder i had 4 folders and i was owner. After upgrade of ubuntu, all folders in /mnt are now properties of ROOT. if i type sudo chown alain:alain /mnt/work, after a computer restart everything is back to root:root as owner. Why?
This issue avoid my fstab mounted share folders to be mounted as i'm not the owner but ROOT.

therefore:
```
//n4200eco/Perso    /mnt/perso    cifs comment=systemd.automount,iocharset=utf8,credentials=/home/alain/.smbcredentials,uid=1000 0 0
```

can not be mounted.

2. even if i set temporary myself as /mnt/perso folder, the following fstab line does not work anymore:
```
//n4200eco/Perso    /mnt/perso    cifs comment=systemd.automount,iocharset=utf8,credentials=/home/alain/.smbcredentials,uid=1000 0 0
```

i have now to type:
```
//n4200eco/Perso    /mnt/perso    cifs comment=systemd.automount,vers=1.0,iocharset=utf8,credentials=/home/alain/.smbcredentials,uid=1000 0 0
```

with some vers=1.0, or vers=2.0, or vers=2.1 or vers=3.0... that basically i still did not understand the purpose...

3. anyway, even i do that step (2), over 4 samba shares from the same NAS with the same rights, only 2 can be mounted.... why ? whereas before upgrade to ubuntu 17.10 and therefore to kernel 4.13, all 4 samba shares were perfectly working as mounted foldes ?
the funniest thing is the answer from ubuntu telling me:
```
[FONT=monospace][COLOR=#000000]sudo mount -a[/COLOR]
Couldn't chdir to /mnt/work: No such device
Couldn't chdir to /mnt/perso: No such device
[/FONT]
```

while all 4 shared folders are on the same NAS, and i fixed "temporary" all ownership of /mnt folders.

thx for your feedback.

---

