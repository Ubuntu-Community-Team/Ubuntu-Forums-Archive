---
title: "Failed dist-upgrade"
date: 2005-10-18
forum: General Help
---

### Post by Riverside on 2005-10-18
anthony@trafford:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]            
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release.gpg [189B]                   
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Sources
Fetched 3B in 0s (9B/s)  
Reading package lists... Done

anthony@trafford:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libgphoto2-2 libgphoto2-port0
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 686kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main libgphoto2-port0 2.1.6-1ubuntu6.1
  404 Not Found [IP: 82.211.81.167 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main libgphoto2-2 2.1.6-1ubuntu6.1
  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-port0_2.1.6-1ubuntu6.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-port0_2.1.6-1ubuntu6.1_i386.deb)  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-2_2.1.6-1ubuntu6.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/libg/libgphoto2/libgphoto2-2_2.1.6-1ubuntu6.1_i386.deb)  404 Not Found [IP: 82.211.81.167 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Any thoughts on how this can be remedied?

---

### Post by ecobuntu on 2005-10-18
just retry again in a half an hour...it's an issue with the ubuntu repositories

---

### Post by Narf on 2005-10-18
Would apt-get dist upgrade corrupt any of my existing data on Hoary?

---

### Post by Murgle on 2005-10-18
it will overwrite your existing programs with the same name, but it won't matter until it gets past the download part and actually starts unpacking the files.

---

