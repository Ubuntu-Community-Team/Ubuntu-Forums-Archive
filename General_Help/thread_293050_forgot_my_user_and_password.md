---
title: "forgot my user and password"
date: 2006-11-04
forum: General Help
---

### Post by C.J.T on 2006-11-04
I forgot my user and password. how do i remove the password? i found my laptop  with ubuntu 6 and i forgot how to get in!(btw im my own system admin)

Thanks,
CJT

---

### Post by ebash on 2006-11-04
Reboot the computer and select single-user mode from the grub menu.

Eventually you should have a root prompt.
Do:
```
passwd USER
```

Where USER is the name of your user. Then provide two times a new password. If the two passwords match your user's password will be reseted. 

Reboot into normal mode, do:
```
reboot
```

---

### Post by C.J.T on 2006-11-04
ok, that pry woulda worked too. i just reinstalled ubuntu :)

---

