---
title: "HDD in external usb enclosure dismounts by itself"
date: 2008-02-08
forum: General Help
---

### Post by kingleer on 2008-02-08
I had an external usb thumb drive that was dismounting itself. 

I solved the problem. Everything works fine if I mount stuff manually. 

Unfortunately, I did something that set my USB 2.0 ports to USB 1.0 speeds. 

Anyone have a fix for this?

---

### Post by kingleer on 2008-02-08
I'm fairly sure this isn't a hardware problem.

---

### Post by kingleer on 2008-02-08
Little help? Pretty please?

---

### Post by pointone on 2008-02-08
Have you checked the logs for error messages?

Check /var/log/syslog shortly after you notice this happen.

---

### Post by kingleer on 2008-02-08
> 
Have you checked the logs for error messages?

Check /var/log/syslog shortly after you notice this happen.
 

edit: mounting the thumb drive using a CLI solves the problem.

---

### Post by kingleer on 2008-02-08
In case any noobs are wondering how to do this 

In the terminal type sudo fdisk -l to get a list of all your partitions/drives.

---

### Post by kingleer on 2008-02-08
Pointone, thanks for your help anyway.

---

