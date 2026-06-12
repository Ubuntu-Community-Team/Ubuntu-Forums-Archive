---
title: "Pepper-flash packages failure"
date: 2016-07-01
forum: General Help
---

### Post by frank18 on 2016-07-01
Hi guys; I've been  receiving this pepper-flash packages notification for long time never been able to download it, see pic. any help thanks.this is on Xubuntu 14.04 


[https://postimg.org/image/6pdm5m9l3/](https://postimg.org/image/6pdm5m9l3/)

---

### Post by Impavidus on 2016-07-01
32 bit or 64 bit?

---

### Post by frank18 on 2016-07-01
thanks; 32bit

---

### Post by Dennis N on 2016-07-01
Install the package **adobe-flashplugin**. It continues to provide a 32-bit version of the flash player for Chromium. This works in Ubuntu and its family of distros. To install it, enable Canonical Partners in your software sources and reload. Then it will be available for installation.

---

### Post by frank18 on 2016-07-01
> **Dennis N said:**
> Install the package **adobe-flashplugin**. It continues to provide a 32-bit version of the flash player for Chromium. This works in Ubuntu and its family of distros. To install it, enable Canonical Partners in your software sources and reload. Then it will be available for installation.

Thanks i did that see pic attach.

---

### Post by X-RED_Tech on 2016-07-01
Now, to install
```
sudo apt-get install **adobe-flashplugin**
```

---

### Post by frank18 on 2016-07-01
> **X-RED_Tech said:**
> Now, to install
```
sudo apt-get install **adobe-flashplugin**
```


Thanks X-RED; i did that and it did download , but still no flash-player,see attach.

---

### Post by QDR06VV9 on 2016-07-01
What dose this show from the terminal
```
apt-cache policy pepperflashplugin-nonfree
```

---

### Post by frank18 on 2016-07-01
> **runrickus said:**
> What dose this show from the terminal
```
apt-cache policy pepperflashplugin-nonfree
```



Thanks,i rebooted and now it's working,


 frank@frank-desktop:~$ apt-cache policy pepperflashplugin-nonfreepepperflashplugin-nonfree:
  Installed: 1.3ubuntu1
  Candidate: 1.3ubuntu1
  Version table:
 *** 1.3ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/multiverse i386 Packages
        100 /var/lib/dpkg/status
frank@frank-desktop:~$

---

### Post by QDR06VV9 on 2016-07-01
Great!:)

---

