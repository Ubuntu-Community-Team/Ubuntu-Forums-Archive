---
title: "Live USB Security?"
date: 2013-08-08
forum: General Help
---

### Post by Maximus559 on 2013-08-08
I'm setting up a dedicated headless system to run SETI@home. To reduce noise and power consumption, I'm booting the machine from a 2 GB flash drive (live USB with persistence, not a full install). Everything seems to be working so far; however, I'm a little worried about security. Is it safe for this system to be online 24/7? For example, the default user account doesn't have a password. Is this a potential problem?

---

### Post by sanderj on 2013-08-08
> **Maximus559 said:**
> I'm setting up a dedicated headless system to run SETI@home. To reduce noise and power consumption, I'm booting the machine from a 2 GB flash drive (live USB with persistence, not a full install). Everything seems to be working so far; however, I'm a little worried about security. Is it safe for this system to be online 24/7? For example, the default user account doesn't have a password. Is this a potential problem?

Interesting point. First thoughts:
- with physical access to the (headless) system, you can obviously logon. No security
- from your LAN: as long as SSH-server is not running, there is some security
- from Internet, assuming there is a NAT-device (=read: router), you can't access the device, so quite high security
- In my experience, it's impossible to update a USB-stick live-Ubuntu (often too little disk space), so that makes it vulnerable

---

### Post by Netstatus on 2013-08-09
> **sanderj said:**
> 
- In my experience, it's impossible to update a USB-stick live-Ubuntu (often too little disk space), so that makes it vulnerable

I can update my live (l)ubuntu usb just fine. I think it would depend on the size of the flash drive at that point.

---

### Post by SweetAurora on 2013-08-09
Go out and buy a 8GB flash drive and Full install Ubuntu to it. That way you are safe and secure as well as it will be quiet. If you can afford it, get a 16GB or bigger drive and make sure it's fast to speed up boot and use.

---

### Post by Netstatus on 2013-08-09
8GB would be just enough but I wouldn't recommend it.

---

