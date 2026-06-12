---
title: "External harddrive &quot;Transport endpoint is not connected&quot;"
date: 2013-02-22
forum: General Help
---

### Post by IQAndreas on 2013-02-22
Nearly all the time my external harddrive (connected via USB and automatically mounted with fstab) works just fine. But about every three weeks, I the following error message from Nautilus when trying to open the external harddrive:
> **The folder contents could not be displayed.**
Sorry, could not display all the contents of "MyBook": Transport endpoint is not connected

A few minutes ago the external harddrive was working just fine (and along with my computer, has been running fine for three or four days without a reboot). This error started appearing about three months ago, and this is roughly the fourth or fifth time the error has happened.

So far it has always solved itself (I would either restart the computer or remount, I don't remember which one worked)


I want to figure out why this error is happening, is it a software or hardware issue? **How do I go about diagnosing this?** Most importantly, **is there a risk my harddrive is starting to die?**


Here is the relevant part of [FONT="Courier New"]/etc/fstab[/FONT] if it is of any use:
```
# MyBook
UUID=12C23AD8C23AC031    /media/MyBook ntfs-3g    auto,users,exec,rw,iocharset=utf8,uid=1000,gid=1000 0 0

# Hide "WD SmartWare"
#/dev/disk/by-label/WD\x20SmartWare /mnt/smartware auto auto,users,exec,rw,iocharset=utf8,uid=1000,gid=1000 0 0
```

---

