---
title: "Unmounting"
date: 2006-07-01
forum: General Help
---

### Post by Firecub on 2006-07-01
1.How to I get rid (Unmount) the SDA1 that ubuntu created for me on the top left corner of the desktop? When I try to unmount it it gives me an error that I don't have sufficient privileges? But I am giving the correct root password! I just don't want to see it there (On my desktop). I really don't want to unmount it if I don't have to? 
Much thanks

---

### Post by aysiu on 2006-07-01
```
sudo umount /dev/sda1
```

---

### Post by Firecub on 2006-07-01
Aysiu! It is people like you who make this world a better place!

Now will I loose any functionality by doing it? 


Thanks!

---

### Post by aysiu on 2006-07-01
It appears you've already lost some functionality.

Ordinarily, you should be able to just right-click the device and unmount it or eject it by selecting the option.

---

### Post by scxtt on 2006-07-01
if you don't want it to be automatically mounted at boot, comment out the line that refers to /dev/sda1 in /etc/fstab ... or if you want it to mount somewhere, but not put an icon on the desktop, mount it somewhere other than /media ... i think it's also possible to tell gconf that you don't want any desktop icons ...

---

