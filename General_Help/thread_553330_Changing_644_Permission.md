---
title: "Changing 644 Permission"
date: 2007-09-17
forum: General Help
---

### Post by bij33 on 2007-09-17
Hi,

Is there a way to change the permission of "fstab" from 644 (-rw-r--r--) to 744 (-rwxr--r--) via chmod command? I am logged in as root and the system does not allow the operation.............Thanks for the help.

---

### Post by logos34 on 2007-09-17
Why would you want to do that?  Fstab is a text configuration file, not some .bin or other executable file

---

### Post by bij33 on 2007-09-17
My original fstab got corrupted somehow and I need to copy the fstab.bak to fstab. That is why I need the rwx permission for Root to be able to copy it.

---

### Post by Slim Odds on 2007-09-17
> **bij33 said:**
> My original fstab got corrupted somehow and I need to copy the fstab.bak to fstab. That is why I need the rwx permission for Root to be able to copy it.

the eXecutable bit has nothing to with copying.

try: ```
sudo cp fstab.bak fstab
```but you had better backup first.

---

### Post by bij33 on 2007-09-17
cp: cannot create regular file 'fstab' : Read-only file system.

This is the message I get after typing "sudo cp fstab.bak fstab" .

FYI, I am in recovry session.


_**Update**_

Tried "mount / -o rw,remount" , that gets filesystem RW back in order.

[SOLVED]

---

