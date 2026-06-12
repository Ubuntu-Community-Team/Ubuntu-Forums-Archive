---
title: "Mounting to see my hdb drive"
date: 2007-02-15
forum: General Help
---

### Post by geovino on 2007-02-15
I'd like to see my hdb drive which is PCLOS in Network servers like my hda1 drive which is Winxp.

I tried this command but it didn't work:

davek@davek-desktop:~$ sudo mount /dev/hdb
Password:
mount: mount point /mnt/pclos does not exist
davek@davek-desktop:~$ 

I've looked in my /mnt file and it's empty. 
What do I add to the fstab file to see the hdb drive?

Thanks

---

### Post by charl.ie on 2007-02-15
```
sudo mkdir /mnt/pclos
```

Hopefully that should fix it :)

---

### Post by geovino on 2007-02-15
OK, I did that, it added the PCLOS dir to the mnt directory, but what do I have to do to show an icon for PCLOS in the Network Servers window like I have for Winxp so I can read the files?

---

