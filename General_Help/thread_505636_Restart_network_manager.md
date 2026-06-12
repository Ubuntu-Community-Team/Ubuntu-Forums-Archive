---
title: "Restart network manager"
date: 2007-07-20
forum: General Help
---

### Post by stchman on 2007-07-20
Hello all, I have a small issue with wireless.

When I boot my laptop up about every 10 or so boot ups network-manager-gnome will not be functioning correctly.  I reboot and all is well.  Is there a way to restart network manager from the command line as a reboot takes time?

Thanks

---

### Post by rscott5 on 2007-07-20
Do you mean just restart the network? You can run
```
sudo /etc/init.d/networking restart
```
to restart all of the networking on the system.

---

### Post by stchman on 2007-07-20
> **rscott5 said:**
> Do you mean just restart the network? You can run
```
sudo /etc/init.d/networking restart
```
to restart all of the networking on the system.

Thank you, I will give that a try when I get home.

---

### Post by stchman on 2007-07-21
That worked!!!!!

Thanks.

---

### Post by rscott5 on 2007-07-22
You're very welcome. Cheers!

---

