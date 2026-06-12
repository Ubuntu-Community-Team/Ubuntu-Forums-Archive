---
title: "acpid won't start"
date: 2007-02-12
forum: General Help
---

### Post by bjdekruif on 2007-02-12
Hello all, 

I run a Ubuntu 6.10 at an AMD64 and I got (nearly) everything working as I want it to. The only thing that will not start is the acpi daemon. In /var/log/boot it gives the following error:

acpid: can't open /proc/acpi/event: Device or resource busy

So it seems that some one opened this file before acpid could open it. If I start Ubuntu in recovery mode, than I can manually start it without any problems.

Does anyone know how I can get acpid to start?

Thanks

bas

---

### Post by Lili on 2007-02-14
> **bjdekruif said:**
> Hello all, 

The only thing that will not start is the acpi daemon. In /var/log/boot it gives the following error:

acpid: can't open /proc/acpi/event: Device or resource busy


Hello, 
i solved with a 

sudo killall hald
sudo /etc/init.d/acpid stop
sudo dpkg --configure -a

Take a look to this thread too: [http://ubuntuforums.org/showthread.php?t=288536](http://ubuntuforums.org/showthread.php?t=288536)

---

### Post by b0b0b0b on 2007-06-04
thanks for posting this, it helped me.

---

