---
title: "Updater has locked me out"
date: 2008-04-23
forum: General Help
---

### Post by Bazza1nolten@swiftdsl.com on 2008-04-23
I downloaded todays updates.23.4.08
Part way through the through the instillation process we had a power failure.
Now the updater is locked and I cannot update or install anything.

The error message I get is
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

when I try to run that I get another error message
 dpkg --configure -a
dpkg: requested operation requires superuser privilege

I am stumped.
Can anyone help me. I don't want to have to reload Ubuntu as I will lose too much.

bazza1

---

### Post by ryanhaigh on 2008-04-23
Use this:
```
sudo dpkg --configure -a
``` 
Messing with packages requires administrator/root priviliges.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) << this is a link

---

### Post by Bazza1nolten@swiftdsl.com on 2008-04-24
Thank you very much.
The code  " sudo dpkg --configure -a " fixed all my updating problems
Bazza1:)

---

