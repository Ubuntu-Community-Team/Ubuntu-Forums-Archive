---
title: "Getting a USB swap disk to automatically run on boot."
date: 2016-07-11
forum: General Help
---

### Post by pandoragami on 2016-07-11
Hello all,

So far I edited my fstab as recommended by many many websites as

```
/dev/sda1 none   swap    sw      0       0
```

I also tried ```
UUID=3261fa40-7715-46f6-a27a-057391c3ca1b 
```in place of ```
/dev/sda1 
``` and when I tried to boot I got a message saying 

check **systemctl status dev-sda1.swap** because of a dependency.

I then used bash to type the message and got.

 ```
dev-sda1.swap - /dev/sda1
   Loaded: loaded (/etc/fstab; bad; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2016-07-11 16:33:43 CDT; 2h 57min ago
     What: /dev/sda1
     Docs: man:fstab(5)
           man:systemd-fstab-generator(8)
  Process: 881 ExecActivate=/sbin/swapon -o sw /dev/sda1 (code=exited, status=255)


Jul 11 16:33:43 pandoragami-desktop systemd[1]: Activating swap /dev/sda1...
Jul 11 16:33:43 pandoragami-desktop swapon[881]: swapon: /dev/sda1: read swap header failed
Jul 11 16:33:43 pandoragami-desktop systemd[1]: dev-sda1.swap: Swap process exited, code=exited status=255
Jul 11 16:33:43 pandoragami-desktop systemd[1]: Failed to activate swap /dev/sda1.
Jul 11 16:33:43 pandoragami-desktop systemd[1]: dev-sda1.swap: Unit entered failed state.

```

Basically the only way I can mount my USB swap is to go into the gnome disks tool and then mount it where it asks for the password for root. 
I'm wondering if that's the dependency?


Thanks!

---

### Post by &amp;KyT$0P# on 2016-07-11
sda1 is usually a partition on your first internal HDD or SSD, not a USB.  Double-check the device name in the GNOME Disk utility, and replace sda1 with that in the fstab.
Does it work then?

---

### Post by pandoragami on 2016-07-11
> **halogen2 said:**
> sda1 is usually a partition on your first internal HDD or SSD, not a USB.  Double-check the device name in the GNOME Disk utility, and replace sda1 with that in the fstab.
Does it work then?

Yes it does, funny thing is is that I tried that before and it didn't work but this time it did. Thanks, it's solved.

---

### Post by &amp;KyT$0P# on 2016-07-11
You're welcome :KS

---

