---
title: "Write-Protection"
date: 2008-02-21
forum: General Help
---

### Post by Timn on 2008-02-21
Hello Everyone,

Not sure if this is the correct place to post this but it seems to be the best place to me. I have some thumb drives that have images (.imz) on them for my forensics class.  I need to mount these thumb drives with write-protection but could not find either a command to do it or a program to just flat out write-protect all usb drives. Anyone know how to do this?

Thanks,
Timn

---

### Post by taurus on 2008-02-21
What format is your USB thumbdrive?  Some drives have a little thing on the side that can lock (write protected) or unlock.  Otherwise, mount it with read-only then.

---

### Post by mrsteveman1 on 2008-02-21
There are 2 issues here, first some drives expose a write lock switch (this is part of the controller chip in the stick itself, not something the OS can control), this effectively prevents any block on the flash device from being written at all. This would be similar to the forensic workstation drive bays with write lock switches on them etc, its entirely hardware based.

If you can't do that, you can in fact mount a drive read only in linux like this:

```
sudo mount -o ro /dev/sda1 /mountpoint
```

Or, if its an image on an already mounted filesystem you can loop mount it read only like this:

```
sudo mount -o ro,loop /home/user/image.imz /mountpoint
```

---

### Post by Timn on 2008-02-21
Thanks for both your replies. I was able to mount the drives read-only perfectly. I was a bit of a noob on this one. Even though I have been using Ubuntu for quite some time now, I am new to using it as a forensics box and was used to having to run a program to write protect the drives in Windows. As usual I looked over the simple approach.

Thanks again,
Timn

---

