---
title: "[SOLVED] No Desktop"
date: 2007-08-09
forum: General Help
---

### Post by jimmyjean on 2007-08-09
Hi

My computer froze during shutdown so I turned the power off. Next time I booted I had the following message:

    kinit:name_to_dev_t(/dev/disk/by_uuid/*****************) = sda3(8/3)
    
    kinit: trying to resume from /dev/disk/by_uuid/**************

    kinit: no resume image, doing normal boot.

Now I always have to use the $xstart command to get my desktop back. When I press the quit icon in the desktop the icons for restart and shutdown have been removed also. I have to shutdown the system manually via the shell.

Does anyone know what has gone wrong?

Thanks

Jim

---

### Post by aysiu on 2007-08-09
I wouldn't worry about the *kinit* message. It's doing a normal boot.

Do you use Kubuntu or Ubuntu?

---

### Post by jimmyjean on 2007-08-09
I use Ubuntu Feisty Fawn 7.04. Thanks

---

### Post by aysiu on 2007-08-09
Can you try this? ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
```

---

### Post by jimmyjean on 2007-08-09
That worked perfectly. The desktop appears on boot now and the icons have reappeared. What was the problem?

Thanks a lot

---

### Post by aysiu on 2007-08-09
Perhaps GDM (the login screen display manager) didn't get shut down properly?

---

### Post by jimmyjean on 2007-08-09
Yeah, I think that was the case, Cheers for your help

---

