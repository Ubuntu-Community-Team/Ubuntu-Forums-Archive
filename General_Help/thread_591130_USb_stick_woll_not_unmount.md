---
title: "USb stick woll not unmount"
date: 2007-10-25
forum: General Help
---

### Post by Argus on 2007-10-25
I have a 1gb KINGSTON USB stick that I use for work. When I plug it in to my computer at home running Ubuntu it will mount properly but I cannot unmount it. I have tried right clicking on the icon, and using the umount command but I get an error that there is a application running. I had this problem in both 7.4 and 7.10.

I have also tried the USB stick in a computer at work running Fedora and it works properly.

Any assistances would be appreciated.

Thanks

---

### Post by taurus on 2007-10-25
Sounds like something is still accessing your drive.  What happens if you run this command from a terminal?

```
sudo umount /dev/sda1 (assuming /dev/sda1 is your USB thumbdrive)
```

---

### Post by Argus on 2007-10-25
> **taurus said:**
> Sounds like something is still accessing your drive.  What happens if you run this command from a terminal?

```
sudo umount /dev/sda1 (assuming /dev/sda1 is your USB thumbdrive)
```

This is what I get;

sudo umount /dev/sda1
umount: /media/KINGSTON: device is busy
umount: /media/KINGSTON: device is busy

sudo umount -l /dev/sda1 works but i kind of defeats the purpose.

---

