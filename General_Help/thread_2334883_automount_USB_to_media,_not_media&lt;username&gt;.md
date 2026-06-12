---
title: "automount USB to /media, not /media/&lt;username&gt;"
date: 2016-08-23
forum: General Help
---

### Post by rawlins02 on 2016-08-23
Just recently installed 16.04. I'm trying to force the mount of USB drives to be /media, as with Ubuntu 12.04 and prior, not the /media/<username> that it creates now. I see many solutions posted in various forums. I tried creating a soft link 

```

ln -s /media/rawlins /media

```

but may have made a mistake. Anyone know of a proper workaround?

---

### Post by Keith_Helms on 2016-08-23
You would need to remove the existing /media/username directory before you try and create the softlink.

---

### Post by Keith_Helms on 2016-08-23
You could also try the udev rule described in this discussion:

[http://askubuntu.com/questions/214646/how-to-configure-the-default-automount-location](http://askubuntu.com/questions/214646/how-to-configure-the-default-automount-location)

---

### Post by rawlins02 on 2016-08-23
> **Keith_Helms said:**
> You could also try the udev rule described in this discussion:

[http://askubuntu.com/questions/214646/how-to-configure-the-default-automount-location](http://askubuntu.com/questions/214646/how-to-configure-the-default-automount-location)


I see that in fact I'd implemented that udev rule method on another machine some time ago. Just checked it and confirmed. I knew I'd enabled something and did not recall using a symbolic link. I'll try the udev solution first thing tomorrow.

---

