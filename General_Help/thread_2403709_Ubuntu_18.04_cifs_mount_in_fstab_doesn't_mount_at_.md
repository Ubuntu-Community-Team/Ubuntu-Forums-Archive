---
title: "Ubuntu 18.04 cifs mount in fstab doesn't mount at boot"
date: 2018-10-15
forum: General Help
---

### Post by Scott_Lindner on 2018-10-15
I'm using the following entry in /etc/fstab to automount a CIFS share.
```
//192.168.1.2/share  /mnt/media      cifs    username=user,password=pass,vers=1.0,_netdev,x-systemd.automount  0  0
```

This will mount with "mount -a" and "mount /mnt/media" fine. However, it will not automount on boot.

More interesting is that I have three servers this entry work on and two it does not work on. All are Ubuntu 18.04 with the latest updates mounting the same share on the same network. The only difference I can come up with between these two sets of servers is that the ones that work were initially Ubuntu 16 boxes that were upgraded to Ubuntu 18 and the ones that do not work were direct Ubuntu 18.04 installs. I checked the logs and didn't see much interesting but I'm guessing the answer is in there somewhere and I don't know what I'm looking for (yet).

Any ideas what could be causing this?

---

### Post by nlee2 on 2018-10-15
Please describe how you determine that the fstab entry does not work. Systemd automount  only generates services at boot. Mounting occurs on use.

---

### Post by Scott_Lindner on 2018-10-15
I was using "df" but based on your post I tried accessing the mount point and it did automount. So now what's interesting is why is are my other two boxes automounting before use? Either way, it works sufficiently. I didn't know there was such a thing in fstab as a lazy automount.

---

