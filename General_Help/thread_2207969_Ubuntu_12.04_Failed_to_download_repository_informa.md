---
title: "Ubuntu 12.04: Failed to download repository information"
date: 2014-02-26
forum: General Help
---

### Post by bardu on 2014-02-26
W:Failed to fetch [https://launchpad.net/~yorba/+archive/ppa/dists/precise/main/source/Sources](https://launchpad.net/~yorba/+archive/ppa/dists/precise/main/source/Sources)  
, W:Failed to fetch [https://launchpad.net/~yorba/+archive/ppa/dists/precise/main/binary-amd64/Packages](https://launchpad.net/~yorba/+archive/ppa/dists/precise/main/binary-amd64/Packages)  
, W:Failed to fetch [https://launchpad.net/~yorba/+archive/ppa/dists/precise/main/binary-i386/Packages](https://launchpad.net/~yorba/+archive/ppa/dists/precise/main/binary-i386/Packages)  
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Any ideas?

---

### Post by claracc on 2014-02-26
The url's provided doesn't exist in launchpad (see attached image), you will have to remove or disable them from your /etc/apt/sources.list file.

I suggest you comment these lines in the file, beginning with a # character, then try again ```
sudo apt-get update
```

---

### Post by bardu on 2014-02-26
Yah... these entries made it to the list when I tried to install the latest version of Shotwell, which failed for some missing library.

---

### Post by ibjsb4 on 2014-02-26
Launchpad does not offer a 12.04 ppa.

[https://launchpad.net/shotwell](https://launchpad.net/shotwell)

From the shotwell site:

Shotwell 0.15 is supported on Ubuntu 12.10 (Quantal Quetzal) and later.

[https://wiki.gnome.org/Apps/Shotwell/BuildingAndInstalling](https://wiki.gnome.org/Apps/Shotwell/BuildingAndInstalling)

Is there a reason for not using the supported 12.04 version in the software center?

---

### Post by bardu on 2014-02-26
Thanks, wasn't aware of that.

I got a new Nikon camera and Shotwell didn't work the way as with my old Nikon. However, after letting the camera format the SD card everything was back to normal. So, properly not an issue with Shotwell.

---

