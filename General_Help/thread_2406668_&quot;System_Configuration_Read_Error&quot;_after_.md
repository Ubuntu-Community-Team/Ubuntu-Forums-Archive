---
title: "&quot;System Configuration Read Error&quot; after installing Kubuntu 18.10"
date: 2018-11-23
forum: General Help
---

### Post by e-zombiehero on 2018-11-23
So I have recently replaced the hard drive in my Gateway M16-24 Laptop, which formerly had Windows Vista installed.

I noticed after installing Kubuntu I received this error with the Bios, I do not have access to any Windows device and need to know how on Kubuntu 18.10 I can create a bootable USB to repair this Bios.

Thank you in advance for any assistance you can provide.

---

### Post by HermanAB on 2018-11-24
[https://www.allbootdisks.com/](https://www.allbootdisks.com/)
[https://www.bootdisk.com/](https://www.bootdisk.com/)
[http://www.boot-disk.com/](http://www.boot-disk.com/)

To copy an image to a USB thingy, use dmesg to see the name of the device, then use the good old kitty cat:
```
$ dmesg
Plug it in
$ dmesg
Copy the file to the device identified above 
(It is never sda, probably sdb.  Get it wrong and you will be very disappointed):
$ sudo cat filename >/dev/sdb
```

---

### Post by e-zombiehero on 2018-11-24
Pirating Windows is not the answer I was looking for,  either way, futher viewers can disregard, the laptop bricked this evening.

---

