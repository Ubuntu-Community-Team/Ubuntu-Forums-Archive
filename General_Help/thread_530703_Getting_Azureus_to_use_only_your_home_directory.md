---
title: "Getting Azureus to use only your home directory"
date: 2007-08-20
forum: General Help
---

### Post by noerrorsfound on 2007-08-20
I'm out of space on my root (/) partition but I have Azureus set up to download to my home directory, which has plenty of space.

Whenever I try to open a torrent in Azureus, it tells me:
> Ensure sufficient temporary file space available (check browser cache usage).
It's trying to write things to my root directory, when it's not supposed to. I had downloaded Xfce but after removing all the packages completely, I'm still out of space on /. I assigned 10 gigabytes for root and aptitude doesn't seem to actually remove files, because after removing gnome-games and all Xfce stuff, my login screen still looms like Xfce and no space has been freed. I'm using the "completely remove" option.

---

### Post by taurus on 2007-08-20
I think it is trying to write some temp files to /tmp which of course, is part of / so you need to free up some space.

```
sudo aptitude clean
df -h
```

---

### Post by noerrorsfound on 2007-08-20
I had already done "aptitude clean" and some other one with "clean" it it, but it does nothing.
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5             9.9G  3.2G  6.3G  34% /
varrun                502M  104K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M   96K  502M   1% /proc/bus/usb
udev                  502M   96K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   39M  464M   8% /lib/modules/2.6.20-16-generic/volatile
/dev/hda6             136G  109G   22G  84% /home

```
I just need to get Azureus to write temporary files to my home directory. Aptitude won't actually delete any packages and since my root partition is before my home, I don't think I can take any space from home for root.

Ubuntu shouldn't need more than 10 gigabytes, anyway... Gentoo was fine with only that much.

---

