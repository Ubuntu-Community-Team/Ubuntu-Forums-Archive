---
title: "need help please to install flash"
date: 2012-11-12
forum: General Help
---

### Post by mrgary on 2012-11-12
here is my problem. i,m running ubuntu 12.4  i need to download. adobe flash player. when i try it pops up choose . dont know what  program to choose. please help.

---

### Post by techvish81 on 2012-11-12
> **mrgary said:**
> here is my problem. i,m running ubuntu 12.4  i need to download. adobe flash player. when i try it pops up choose . dont know what  program to choose. please help.

install "ubuntu restricted extras" from the software centre. you will get all the things required to handle media on your system.  ( along with the flash plugin).

---

### Post by Abhinav Kumar on 2012-11-12
> **mrgary said:**
> here is my problem. i,m running ubuntu 12.4  i need to download. adobe flash player. when i try it pops up choose . dont know what  program to choose. please help.
Hi mrgary,
You can try installing flash in some other way too. 
Go to adobe site 
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
and download flash player as tar file.

Now extract the contents of tar file using archive manager.

say you extracted and you created folder named install_flash at the Desktop.
You can see there will be a file named libflashplayer.so in install_flash folder.
execute the following command in terminal

```

sudo cp ~/Desktop/install_flash/libflashplayer.so /usr/lib/mozilla/plugins/

```
and then give the password

Regards,
ABhinav

---

### Post by Impavidus on 2012-11-13
Normally you should install flash player via the software centre (or synaptic, apt-get, anyway, from the repos). Sometimes this doesn't work. Only in the rare occasions that you're stuck with an outdated flash version you should install manually.

---

### Post by philinux on 2012-11-13
> **mrgary said:**
> here is my problem. i,m running ubuntu 12.4  i need to download. adobe flash player. when i try it pops up choose . dont know what  program to choose. please help.

You need to forget the windows way of downloading software. Ubuntu has 99% of all the apps you need on it's own servers. Or it will install it for you from say adobe in this case via the ubuntu-restricted-extras. Open the software center and search for flash.

See this guide. [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

