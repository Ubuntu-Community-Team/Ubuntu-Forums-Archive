---
title: "need help cd rom drive says not mounted"
date: 2008-05-03
forum: General Help
---

### Post by eletrixmike on 2008-05-03
Like the title says can someone pls help me get my drive working so i can load up from it. It didnt load up on install. Im new to all this so I need direct directions as to how t g about fixing it. Thanks!

---

### Post by eletrixmike on 2008-05-03
mount: special device /dev/scd0 does not exist

unable to mount selected volume

---

### Post by DBrocks on 2008-05-03
```
sudo mount /dev/cdrom /cdrom
```

---

### Post by eletrixmike on 2008-05-03
sudo mount /dev/cdrom /cdrom
[sudo] password for michael:

is that all?

---

### Post by DBrocks on 2008-05-03
when it asks for the password, enter you password. Your cd will then be mounted in "/cdrom"

---

### Post by eletrixmike on 2008-05-03
didnt do nothing still wont read cd

---

