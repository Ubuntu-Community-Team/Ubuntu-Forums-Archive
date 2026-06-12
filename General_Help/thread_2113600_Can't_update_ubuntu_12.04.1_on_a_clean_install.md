---
title: "Can't update ubuntu 12.04.1 on a clean install"
date: 2013-02-07
forum: General Help
---

### Post by Ralph L on 2013-02-07
I just did a clean install of Ubuntu 12.04.1 and then tried to use Update Manager to install all the updates.  My computer is a Dell Latitude D610 laptop.  Update Manager failed with 
```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_2.36.3_i386.deb 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.11.4-0ubuntu10.8_all.deb 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.11.4-0ubuntu10.8_i386.deb 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.99-21ubuntu3.7_i386.deb 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc-bin_1.99-21ubuntu3.7_i386.deb 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub2-common_1.99-21ubuntu3.7_i386.deb 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.99-21ubuntu3.7_i386.deb 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.17.0-1ubuntu4.2_i386.deb 404  Not Found [IP: 91.189.91.15 80]
```

I checked a few of the web sites referenced and indeed the referenced folder/files were not there.  

This is particularly frustrating, because the reason I was doing a new clean install was that performing an update on my previous installation of 12.04.1 broke Suspend and Hibernate.  Now updating my clean install won't work.

Anybody else have this problem?  Any help is appreciated.

---

### Post by zombifier25 on 2013-02-07
Do a
```
sudo apt-get update
```
and try again. If it doesn't work, Open Update Manager > Configure (or settings, I'm not using the English locale) and change your server to the main server, and update again.

---

### Post by Ralph L on 2013-02-08
Thanks Zombifer25.

That worked, although I still don't understand what went wrong.

---

