---
title: "Write access on vfat partition"
date: 2006-11-07
forum: General Help
---

### Post by indytim on 2006-11-07
I've got a vfat mounted partition which I'm able to read ok.  Having difficulty establishing a mount so that I can write to it.

Here's the line from the fstab on the partition:
```
/dev/sda11      /media/sda11    vfat    defaults,utf8,umask=007,gid=46 0       1
```

when I invoke nautilus to root level for each folder in the partition, the permissions are set at
File Owner : root
File Group : plugdev

Within the pulldown for each of the above, I can select my user id.  However, when I try to set it to my id, it crabs saying I don't have permission to change the access (even though I'm at root level on nautilus).

Appreciate any feedback on getting this resolved as this is the gateway between the Windows apps and my Linux work.

Thanks,

IndyTim

---

### Post by taurus on 2006-11-07
Change that line to 

```

/dev/sda11      /media/sda11    vfat    defaults,utf8,umask=000    0   0

```
Then reboot...

---

### Post by Joe_CoT on 2006-11-07
set the umask to umask=000

---

### Post by indytim on 2006-11-07
Thanks to both of you.  It is now resolved.  

IndyTim

---

### Post by TadeusDeLotanar on 2006-11-22
Sorry for bringing this up again, but I have the same problem with my fat32 Partition, here part of my fstab:

```

/dev/sda4       /home/zwirnfx/Daten     vfat    defaults,iocharset=utf8,umask=000       0       0

```

Once the partition is mounted the folder owner/group are changed to root.

I'am using EdgyEft on an X60s Thinkpad.

I hope someone can help my.

I just changed it to

```

/dev/sda4       /home/zwirnfx/Daten     vfat    user,iocharset=utf8,umask=000       0       0

```

and hat write access for about 1 minute. If I mount the partition manualy, I'm told, that I can't write on a write protectet drive.

---

