---
title: "About fastboot"
date: 2014-11-01
forum: General Help
---

### Post by charitosha on 2014-11-01
Hello everyone,
Didn't really wanted to post this in xda because it's a bit ubuntu related....
So i have ubuntu 12.04, from this link: [http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/](http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/)
i installed, without problems, the ubuntu-device-flash-package in order to get adb and fastboot (well not only for this, but that's another story). 

Now if i'm not mistaken the device-flash-package man pages say that it beenn made for nexus. (i don't have nexus but an old motorola droid 2 global).
However  adb and fastboot should work on all devices. if i type in the terminal *abd help 2>&1 | less *i get the adb help pages, if i type in the terminal 
*fastboot help 2>&1 | less* i get the fastboot help pages. However the fastboot codes are not working.....

adb is working fine, but when the phone is in the bootloader (by pressing the keys on the phone) fastboot is not responding...
e.g. when in bootloader, if *fastboot devices* is typed in the terminal there is no response.

Can anyone help me somehow with this situation?

---

### Post by charitosha on 2014-11-02
I went through the installation again so i can copy the replies of each line of codes.
the problem arises at installing the ubuntu-device-flash-package step:
```

sudo apt-get install ubuntu-device-flash
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```
Now i'm pretty sure that the universe archive is enabled and i didn't had any problem adding the PPAs...

P.S. however i can see the man pages of ubuntu-device-flash (via the terminal)

---

