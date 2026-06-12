---
title: "Kubuntu 18.04 /etc/fstab failed to mount"
date: 2018-08-04
forum: General Help
---

### Post by alynur2 on 2018-08-04
Hello all, being new to KDE, I was unaware of KDE's mounting protocols of other partitions and tried to auto mount my DATA partition by editing the fstab file as I normally do in other ubuntu distros. So now when I attempt to boot, it boots into emergency mode and typing journalctl -xb shows the /etc/fstab failed to boot. Using nano /etc/fstab enables me to remove the edits i had made but upon rebooting I get back into the same cycle with the same /etc/fstab failed to boot error. Aside from a fresh install, is there any way of fixing this? A fresh install is no big deal but if there is a way of fixing it I would love to learn how. My ubuntu knowledge is limited and I would greatly appreciate learning something new.

---

### Post by Dennis N on 2018-08-04
To automount an ext4 data partition at /mnt/Data, I add this line to my /etc/fstab: 

```
UUID=d97e2feb-1bf6-429b-bba5-943264ec1474 /mnt/Data ext4 defaults 0 2
```

You can modify it with the UUID of the partition to be mounted, and the mount point to use.

You could also post your fstab contents for others to view for obvious errors.

---

### Post by alynur2 on 2018-08-04
Hi Dennis N, the code I had was this;
> UUID=585c3e2f-c6be-4802-885d-eead48242766 /mnt/DATA  ext4
defaults,discard  0  2

What I really want to know is how do I get the fstab to mount even without the code I had added? I removed everything I added and I still can't boot up.

---

### Post by oldos2er on 2018-08-04
Is this an SSD or an HDD?

---

### Post by alynur2 on 2018-08-04
Okay I found my problem. I somehow inadvertently commented the first line, removed the #. After correcting that, I then went ahead and added my code back in minus the ",discard" to keep it aligned with Dennis N's code and it works. I'm back in Kubuntu 18.04 with my DATA partition mounted automatically!

---

