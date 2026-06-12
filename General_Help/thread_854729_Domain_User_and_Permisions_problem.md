---
title: "Domain User and Permisions problem"
date: 2008-07-09
forum: General Help
---

### Post by thieves.honor on 2008-07-09
I have ubuntu 8.04 install.  I used likewise open to join it to my domain at work.  I have barry install so that I can sync my blackberry with evolution.  As a regular user I can accomplish this without a problem.  when I login to the domain I get the following error message:  
Usb::Error caught: (-1, error sending control message: Operation not permitted): Probe: GetConfiguration failed

I manually edited /etc/group and added the domain user to all the same groups that my local user is in.  I can now run the sudo command without switching to the local user first, but I still get the same error message with barry.

anyhelp would be appreciated.

---

