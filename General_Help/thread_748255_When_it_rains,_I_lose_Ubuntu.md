---
title: "When it rains, I lose Ubuntu"
date: 2008-04-07
forum: General Help
---

### Post by jefuchs on 2008-04-07
This has happened twice in a week.  A thunderstorm passes through, the electricity flickers, and Ubuntu won't boot anymore.

Since recovery mode is useless for non-techies, I've had to re-install Ubuntu twice in a week.  It seems to get stuck at /usr/rc.local, or the file that's supposed to come after it.

I have two computers.  My old one runs Dapper Drake, and seems immune to problems.  Reboots fine after a power interruption.  The new one has Gutsy Gibbon and can't boot after a storm.

Any ideas?

Bonus question:  When I installed the OS I made a point of having my /home directory mounted on a separate physical drive.  I did this during installation.  Now that I have re-installed, how can I re-mount that drive as /home?

Thanks.

---

### Post by MONODA on 2008-04-07
well I have also realized that ubuntu is quite vulnerable to power shortages. anyway, when you reinstalled, you should have selected that mountpoint for your old /home as /home. you should be able to mount it as a normal drive like you would with any other drive or with:
> sudo mkdir /media/old/home && sudo mount /dev/sdax /media/oldhome
x stands for whatever partition your old /home is.

---

### Post by mali2297 on 2008-04-07
> **jefuchs said:**
> It seems to get stuck at /usr/rc.local, or the file that's supposed to come after it.


That's right before the GUI should start. 

Change to another virtual console by pressing Ctrl+Alt+F2. Login, then try starting the GUI with
```

startx

```

---

### Post by jefuchs on 2008-04-07
> **MONODA said:**
>  when you reinstalled, you should have selected that mountpoint for your old /home as /home.:



I was afraid that it would have re-formatted the drive.  No?

---

### Post by MONODA on 2008-04-07
depending on how you installed ubuntu, did you erase all your drives?

---

### Post by jefuchs on 2008-04-07
> **MONODA said:**
> depending on how you installed ubuntu, did you erase all your drives?

No, but I was worried the partitioner would erase all the drives I specified, including the home drive.

---

### Post by tamoneya on 2008-04-07
you just need to add that drive to /etc/fstab
```
/dev/sda1 /home ext3 defaults 0 0
```
This is assuming that your old home partition was /dev/sda1 and that it is formated as ext3

---

