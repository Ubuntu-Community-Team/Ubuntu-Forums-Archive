---
title: "Fiddled with xorg.conf"
date: 2008-02-07
forum: General Help
---

### Post by Dojan5 on 2008-02-07
Okay...
This aint good...
I changed the default depth and the highest screenresolution in xorg.conf...
Not a good idea...
Now i use the live session...
Help me.
How to i save the file in XORG.conf???

>>>Edit<<<
Oh yaa, i use live session too

---

### Post by bodhi.zazen on 2008-02-07
1. Alyays back up system files befor you edit them.

2. Boot to recovery mode and :

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Dojan5 on 2008-02-07
> **bodhi.zazen said:**
> 1. Alyays back up system files befor you edit them.

2. Boot to recovery mode and :

```
dpkg-reconfigure -phigh xserver-xorg
```

I did make a backup...
But it got so sever so i can't get into GNOME.
The copy is on the desktop....

Anywho, im editing the partitions right now,, (to get it done since i was already planning to do so... So thanks)

Joel

---

### Post by bodhi.zazen on 2008-02-07
OK, if you made a backup, you can restore it from the command line :

```
sudo cp /path/to/backup /etc/X11/xorg.conf
```

Then restart GDM

```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

---

### Post by Dojan5 on 2008-02-07
I cant enter safe recovery mode, it just continue booting as normal.
I can only get a terminal in the Live CD
Are there any way of restoring the XORG.conf in a live session???

---

### Post by bodhi.zazen on 2008-02-08
Boot the live CD

Mount your ubuntu root partition at say /media/ubuntu

```
sudo mkdir /media/ubuntu
sudo mount /dev/sdxy /media/ubuntu
```

Change "/dev/sdxy" to your ubuntu root partition.

Then you can eiterh :

1. Restore from backup :

```
sudo cp /media/ubuntu/path_to/corg.conf_bakkup /media/ubuntu/etc/X11/xorg.conf
```

Reboot

============

2. Manually reset it :

```
sudo chroot /media/ubuntu /bin/bash
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot

---

### Post by Dojan5 on 2008-02-08
Thank you thankt you thank you!!!!
You solved it for me...
Thus, i manuallt mounted the volume...
Realised that my home directory was in another partition and so i copied the Live CD's xorg.conf to the non-live cd's XORG.conf!!!
Thanks!!!!!!!!!!!!!

---

