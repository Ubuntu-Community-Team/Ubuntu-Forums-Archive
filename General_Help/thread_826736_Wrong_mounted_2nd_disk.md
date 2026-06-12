---
title: "Wrong mounted 2nd disk"
date: 2008-06-12
forum: General Help
---

### Post by doggy style on 2008-06-12
I guess it's an easy issue to cure

I accidently mounted the second disk on the path
/home/lalli
(lalli is the user)
Now to undo this, i tried
sudo umount /home/lalli
Of course an message "disk in use or busy" occured
I tried to solve the issue using webmin.
Without succes becaus it doesn't let you configure a disk
which is currently in use.

Who could possibly help me.

Thanks a lot in advance
kind regards

---

### Post by forger on 2008-06-12
```
sudo umount -a
sudo mount -a
```
or

```
sudo reboot
```

---

