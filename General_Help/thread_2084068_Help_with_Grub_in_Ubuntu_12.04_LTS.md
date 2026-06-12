---
title: "Help with Grub in Ubuntu 12.04 LTS"
date: 2012-11-14
forum: General Help
---

### Post by lumaja on 2012-11-14
It seems there is something wrong with Grub with Ubuntu 12.04 LTS.
 On Shut Down a window flashes with some text but it is to quick to
 read and I think is Grub with problems.
 I need help to fix this please.

---

### Post by carl4926 on 2012-11-14
> **lumaja said:**
> It seems there is something wrong with Grub with Ubuntu 12.04 LTS.
 On Shut Down a window flashes with some text but it is to quick to
 read and I think is Grub with problems.
 I need help to fix this please.

Other than something you can't determine... The system is running OK?

---

### Post by offgridguy on 2012-11-14
> **lumaja said:**
> It seems there is something wrong with Grub with Ubuntu 12.04 LTS.
 On Shut Down a window flashes with some text but it is to quick to
 read and I think is Grub with problems.
 I need help to fix this please.

The text itself may not be indicative of a problem,  I have the same and everything works fine.   Is there something else that may indicate a problem with GRUB?

---

### Post by NikTh on 2012-11-14
Hi , 

to locate shutdown messages is difficult. I don't even know if stored somewhere , because during shutdown system going to sleep and I think no logs kept. 
You can track messages in /var/log/kern.log , but you have to know the message (even a word or something) , because this kern.log is too long (could be 10.000 lines). 

You can try to remove the "quiet splash" options from /etc/default/grub and try again to locate (with your eyes) the failing message. 

```
gksudo gedit /etc/default/grub
```find the line 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
and make it 
GRUB_CMDLINE_LINUX_DEFAULT=""
save the file and run
```
sudo update-grub
```reboot and then reboot again to see the message. 
Also I think you can press [Pause/Break] button during shutdown to freeze the messages , but I'm not sure. Try it.

Thanks

---

### Post by philinux on 2012-11-14
Grub is used to boot the machine and has no part in the shutdown process.  Spurious shutdown messages can be safely ignored. I get them too.

---

