---
title: "Error Occured While Mounting 0 - Ubuntu 13.04 Boot Error"
date: 2013-08-11
forum: General Help
---

### Post by Dallin_Engberson on 2013-08-11
I was messing around in /ect/fstab trying to add swap one day. It wasn't working so I decided to give up and reboot my computer, so I deleted the line for swap and rebooted. On boot up I was greeted by a message that said "Error Occured While Mounting 0" Where it asked me to either skip the booting or manually fix this. Here is my FSTAB:
> 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=3f6522cb-036f-43be-a45f-2085126cd9f0 /               ext4   
errors=remount-ro 0       1


And here is my blkid:
> /dev/sda1: LABEL="System" UUID="9AF6379DF6377919" TYPE="ntfs" 
/dev/sda2: LABEL="TI105847W0E" UUID="01CE94C3668D4170" TYPE="ntfs" 
/dev/sda3: LABEL="HDDRECOVERY" UUID="7A4282624282234D" TYPE="ntfs" 
/dev/sda4: UUID="3f6522cb-036f-43be-a45f-2085126cd9f0" TYPE="ext4" 
/dev/sdb1: LABEL="USB20FD" UUID="6A64-3D4B" TYPE="vfat" 


Thank you in advance!

---

### Post by The-Server-4dmin on 2013-08-11
So you installed with out a swap or are you trying to add more swap. :-k

---

### Post by munkey09 on 2013-08-11
Ubuntu will not boot with a NTFS partition in the Fstab and will boot only when the file system is not unmounted in windows 8, the Ubuntu load screen will only show an infinite loop.

---

### Post by munkey09 on 2013-08-11
if you go into windows and restart immediately ubuntu will start immediately and work but only sometimes.

---

### Post by Dallin_Engberson on 2013-08-11
> **The-Server-4dmin said:**
> So you installed with out a swap or are you trying to add more swap. :-k
There was no swap when I installed and I was trying to add some by creating a 2 gb file in the root and assigning it as swap. I watched a Youtube video where someone tried it and it worked.

---

### Post by steeldriver on 2013-08-11
if your fstab really has a newline between the 'ext4' and the 'errors=remount-ro' 

```

UUID=3f6522cb-036f-43be-a45f-2085126cd9f0 / ext4
errors=remount-ro 0 1 

```

(i.e. it's not just the forum formatting) then you need to remove it - like this

```

UUID=3f6522cb-036f-43be-a45f-2085126cd9f0 / ext4 errors=remount-ro 0 1 

```

---

### Post by Dallin_Engberson on 2013-08-12
Apparently I had pressed enter while removing the swap line. Thank you so much!

---

