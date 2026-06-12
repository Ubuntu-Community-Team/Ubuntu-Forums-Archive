---
title: "network shares not anymore mounted at boot"
date: 2017-01-24
forum: General Help
---

### Post by alain.roger on 2017-01-24
Hi,

since last update and upgrade, my shared network folders are not anymore mounted automatically.
FOr more than 1.5 year all shared folders are mounted using /etc/fstab but not anymore since last upgrade.

however if in terminal i type:
sudo mount -a

all shares folders are mounted...so why does it work in terminal manually and not using /etc/fstab while nothing in fstab changed ?
thx

---

### Post by deadflowr on 2017-01-24
Most likely it's a cart before the horse scenario.
Where as when fstab starts the mounting, you do not have networking up yet.
So since no proper networking up no mounting of networking shares.

I would think two things to help figure this out would be

1)Type of shares: samba or nfs or sftp or other

2)Version/Release of Ubuntu

But that's about as much help as I'll be.
Not that it helps, but hopefully can get the ball rolling.

---

### Post by SeijiSensei on 2017-01-24
If it's a boot sequence issue, the simplest solution is to add the line
```

mount -a

```
to /etc/rc.local, which runs after all the other init scripts have completed.

Notice there is no sudo in that command since /etc/rc.local is run with root privileges by default.

---

### Post by alain.roger on 2017-01-25
After doing several tests, i found the following report : [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1544480](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1544480)

by adding comment=systemd.automount to fstab solved my issue:
[COLOR=#333333][FONT=monospace]e.g.:
//192.168.1.100/shared /media/shared cifs comment=systemd.automount,credentials=…[/FONT][/COLOR]

---

### Post by Keith_Helms on 2017-01-25
You gotta love Linux where an option described as a "comment" actually causes something to get executed.

---

