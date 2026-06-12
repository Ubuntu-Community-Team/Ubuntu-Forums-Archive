---
title: "Installing COD 1"
date: 2008-03-04
forum: General Help
---

### Post by JordanTW90 on 2008-03-04
I'm trying to install Call of Duty 1 on my new linux box through wine.  It works fine until I have to put in disk 2, but it wont let me open the CD drive to swap the discs.

Any help?

---

### Post by -Zeus- on 2008-03-04
try unmounting the drive by running this command:

```
sudo umount /media/cdrom0
```

---

### Post by NullHead on 2008-03-04
I would use this.> wine eject /media/cdrom0

---

### Post by JordanTW90 on 2008-03-04
The wine command doesnt work.  The other tells me that the device is busy.  The program is telling me to put in the other CD.

---

### Post by JordanTW90 on 2008-03-04
Ive tried nearly everything, even went to copy the cd contents to the root and boot up from there.  Even then it says I need CD2 and wont continue.

---

### Post by NullHead on 2008-03-04
Ok try this: > wine eject -a

---

