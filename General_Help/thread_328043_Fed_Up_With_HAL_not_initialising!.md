---
title: "Fed Up With HAL not initialising!"
date: 2006-12-30
forum: General Help
---

### Post by Jose Catre-Vandis on 2006-12-30
Running up to date Dapper on Shuttle SN45G with AthlonXP 1700, IGB ram, 250mg HD

On every boot, I now get the message, "Error, Hal is not initialised" in a dialog box. PC boots up OK, and not hangs there, so this is not the smbfs problem. I have no samba shares, but do have auto links in fstab for my NFS server. This prevents access to some hardware, USB drives, Floppy, CD rom (sometimes), and is getting bl**dy annoying ](*,) 

Can some one please provide a walkthrough for fault finding for this? Much as I enjoy setting up Ubuntu, I would rather stick with this install, 6 months worth of tweaking and sorting.

Thanks

[EDIT]

But it seems that this user has the answer:
[http://www.ubuntuforums.org/showpost.php?p=1857054&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1857054&postcount=4)

I beleive it is a timing issue with the boot up sequence, that gets a little out of sync. the two terminal commands do appear to sort it out. Anyway, this is the first time i have booted in over a week, without the error!  :)  Thanks Heggel

```
sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12
```

---

