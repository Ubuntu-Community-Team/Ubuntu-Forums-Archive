---
title: "Mounting CD/DVD image"
date: 2008-01-27
forum: General Help
---

### Post by werg on 2008-01-27
Is there a package in Ubuntu that allows to mount a disc image (a virtual drive)?

Thanks

---

### Post by taurus on 2008-01-27
Applications -> Accessories -> Terminal
```
sudo mkdir /media/iso
sudo mount -t iso9660 *filename.iso* /media/iso -o loop
ls -la /media/iso
```

---

