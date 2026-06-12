---
title: "Cannot mount LG K8 android phone -Ubuntu Mate"
date: 2016-11-15
forum: General Help
---

### Post by david192 on 2016-11-15
Hi, bit of a newbie, hope you can help, I am trying to connect my phone to my laptop but I keep getting an error - 'Cannot Mount LGE Android Phone - no MTP devices found'. The phone in question has had a factory reset. I have libmtp installed, and I have tried the  Android Debug Bridge tool? but I cannot mount it. It is recognized in lsusb (Bus 001 Device 027: ID 1004:633a LG Electronics, Inc. ) and also in  'Devices' column in my home folder. That's as far as my knowledge goes with this.  Any help would be appreciated, thank you

---

### Post by ajgreeny on 2016-11-15
Which version of Ubuntu-Mate.

16.04 appears to mount Android phones (& tablets?) without any actions on the users part, but 14.04 required a few manual edits of files to do so.

See [https://ubuntuforums.org/showthread.php?t=2226702](https://ubuntuforums.org/showthread.php?t=2226702) if still on 14.04.

---

### Post by david192 on 2016-11-16
Hi, thank you for your reply, not sure of the distro I have but was was recently obtained ( 2 months ago ) so should be recent version? I have tried the steps set out in the link you provided but hasn't made any difference. I did however try a different android phone which DID mount but only showed folders for images but not the image files themselves? I tried a mtp-detect on the LG phone and it returned a 'no raw files detected'  message.
Thanks again

---

### Post by howefield on 2016-11-16
> **david192 said:**
> Hi, thank you for your reply, not sure of the distro

What's the output of

```
cat /etc/*-release
```

---

### Post by jeremy31 on 2016-11-16
I find that I need to go into the phones Developer Settings and enable USB Debugging to even be able to connect and I have to change it from charge only to file transfer.  I haven't had any luck using the USB 3.0 ports on my laptops for some reason

---

### Post by david192 on 2016-11-16
Thank you for your replies. 
howefield - 
Output of cat /etc/*-release is 
```
dt@Laptop:~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
NAME="Ubuntu"
VERSION="16.04.1 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.1 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenial
```

jeremy31 - unfortunately I cannot access any files on the phone as I no longer have that Google account, what i am looking to do is flash the phone so I can use it again.
regards

---

### Post by jeremy31 on 2016-11-17
I have not heard of losing access to a phone because of a google account before.  You may want to search for how to do a factory reset on the phone as I did it once years ago on an Android I gave to my neice

---

### Post by david192 on 2016-11-17
Hi jeremy31, I agree it is strange how I cannot access the phone after a factory reset ( I've done that already ) and my laptop point-blank refuses to mount it, I don't have a Windows machine to see if that makes any difference Thank you for your advice, it's not crucial that I have this phone up and running again so i'll probably leave it for now.

---

