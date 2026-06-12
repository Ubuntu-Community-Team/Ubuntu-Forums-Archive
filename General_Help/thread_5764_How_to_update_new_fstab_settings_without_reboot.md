---
title: "How to update new fstab settings without reboot?"
date: 2004-11-22
forum: General Help
---

### Post by svarreby on 2004-11-22
I have made some changes to my fstab. Do I have to reboot so that these new settings activates or is it possible to do some "CL-magic"?

---

### Post by calvinpriest on 2004-11-22
You don't need to reboot for fstab settings to take effect.  However you do need to mount or re-mount (depending on what you are doing).  The command syntax will be similar, but not the same, to what you put in fstab.  What are you trying to mount?

---

### Post by p!=f on 2004-11-22
After editing the fstab file run
```

sudo mount -a

```

---

### Post by svarreby on 2004-11-22
Thanks for your replies :-)

calvinpriest:  I have added all (5) my NTFS shares on a desktop PC.

p!=f:  THANKS! Just what the doctor ordered :-)

---

