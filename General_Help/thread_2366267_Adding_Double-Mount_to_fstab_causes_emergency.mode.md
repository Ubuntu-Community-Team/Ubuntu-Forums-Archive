---
title: "Adding Double-Mount to fstab causes emergency.mode boot"
date: 2017-07-15
forum: General Help
---

### Post by scambro on 2017-07-15
Not sure if I described that appropriately in the subject.  I have NFS shares setup on a server.  I mount from a UUID, then in fstab, mount that share to a /export/ directory.  It worked when I set it up and ran mount -a, but when I reboot and it starts from scratch, I get an error about finding the UUID in question:

```
# SATA Devices
UUID=1234       /media/serv02bay02      ext4    errors=remount-ro       0       1
UUID=5678      /media/serv02bay03      ext4    errors=remount-ro       0       1

#/media/serv02bay02     /export/bay02   none    bind    0       0
#/media/serv02bay03     /export/bay03   none    bind    0       0
```

I commented out those two lines in the emergency terminal when troubleshooting, and sure enough, it boots normally if I do that.  

I thought this was the appropriate way to create NFS shares.  Should I be mounting this differently?  Should my export lines be mounting directly from the UUID as well?

Thanks!

---

### Post by scambro on 2017-07-15
Scratch that.  I just rebooted again and ended up in emergency mode.  More troubleshooting to do...

---

