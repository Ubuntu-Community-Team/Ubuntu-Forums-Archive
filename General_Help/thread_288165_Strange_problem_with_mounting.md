---
title: "Strange problem with mounting"
date: 2006-10-29
forum: General Help
---

### Post by dentaku65 on 2006-10-29
Hi all,
upgrading from Dapper to Edgy I've encounter this issue:
when I mount a device the device is mounting but I cannot see the icon on the desktop (and the action associated to the device).

I've checked the option volumes_visible under nautilus-desktop in gconf-editor and is set properly, I've removed with purge hal and reinstalled, if I insert for example an USB key and I do this command
```
pmount-hal /dev/sd1
```
it works properly (adding the icon on the desktop and open Nautilus).

This is really annoying because when I insert a cd, an usb key or mounting my ntfs partition I'm always must use computer:// to get the device resources.

Anyone have some hints? TIA
](*,)

---

### Post by dentaku65 on 2006-10-30
This is a WORKAROUND

I've installed ivman
```
sudo apt-get install ivman
```
then:
```
sudo ivman
```

And it works automounting devices as expected Gnome-volume-manager can do... in my case only my NTFS partition in read/write mode have some issue (but is working with umount/mount action)

---

