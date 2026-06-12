---
title: "Hardy switching /dev/sda a /dev/sdb after boot"
date: 2008-04-26
forum: General Help
---

### Post by Kokesh on 2008-04-26
I had this problem since I upgraded to Hardy beta, than it disappeared for some time and now it is here again.

From time to time, after restart, I get error about bad superblock while booting system (switched sda & sdb in fstab). That I continue with boot and switch all sda a sdb entries in fstab (sda1->sdb1 etc) and do **sudo mount -a**. After next reboot, most probably I will have to switch it again and it will stay for couple of next reboots.

It is quite annoying. What could that be?

---

### Post by Rocket2DMn on 2008-04-26
You can replace the entries in fstab to use UUIDs instead which won't cause problems when the device points change.  Please post
```
sudo fdisk -l
cat /etc/fstab
mount
ls -l /dev/disk/by-uuid/
```

---

### Post by Kokesh on 2008-04-27
Thanks, this helped, but still it doesn't solve this problem, I can imagine somebody who have no clue about setting having this problem. It shouldn't switch sda & sdb by itself.

Thanks for solution, it seems works great!

---

### Post by vanadium on 2008-04-27
That is why nowadays it is common practice to use UUID or LABEL in /etc/fstab.

---

### Post by Rocket2DMn on 2008-04-27
Ubuntu usually uses UUIDs by default when it installs the system, so perhaps you added the entries yourself later or modified what was already there?
You can learn more about fstab here: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

