---
title: "Can’t install Intel Graphics drivers"
date: 2017-04-10
forum: General Help
---

### Post by lumaja2 on 2017-04-10
[SIZE=3]Download intel-graphics-update-tool_2.0.3_amd64.deb and  intel-graphics-update-tool_2.0.3_i386.deb.[/SIZE]
 Neither GDebi or Ubuntu Software can install this files.
 Gdebi with error.
 Package: intel-graphics-update-tool
 	    not satisfiable:
 	     libpackagekit-gdib2-18
 	      (>=0.90.4)
 Ubuntu Software center after clicking on install nothing happen.
 Can some one help to install this drives please.
 Thank you

---

### Post by Perfect Storm on 2017-04-10
Try with:
```
sudo apt install packagekit-backend-aptcc
```

---

### Post by mc4man on 2017-04-10
Those intel packages are for 16.10, is that what you're using? (doubtful..

---

### Post by lumaja2 on 2017-04-11
Which is the correct  intel packages for Ubuntu 16.04 i386 and, or 64 Thank you

---

### Post by Perfect Storm on 2017-04-11
```
uname -i
```
What does it say?

for ubuntu 16.04: [https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.2](https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.2)

---

### Post by lumaja2 on 2017-04-12
luis@luis-Ubuntu-16:~$ uname -i i686 luis@luis-Ubuntu-16:~$

---

### Post by Perfect Storm on 2017-04-12
Then you go with 32-bit

---

### Post by lumaja2 on 2017-04-12
When I asked “Which is the correct  intel packages for Ubuntu 16.04 i386” I was asking about what mac4man wrote the packagekit-backend-aptcc was for Ubuntu 16.10. I have the intel packages for Ubuntu 16.04, my problem is as I stated before, installing this. I Need help how to install this int package. Thank you

---

### Post by mc4man on 2017-04-12
> **lumaja2 said:**
> When I asked “Which is the correct  intel packages for Ubuntu 16.04 i386” I was asking about what mac4man wrote the packagekit-backend-aptcc was for Ubuntu 16.10. I have the intel packages for Ubuntu 16.04, my problem is as I stated before, installing this. I Need help how to install this int package. Thank you
I said nothing about  packagekit-backend-aptcc, the intel packages you mentioned (2.0.3) are for 16.10, not 16.04.
As far as the intel installer for 16.04 (2.0.2), it's probably just for 16.04 installs using the release or 16.04.1 images that haven't upgraded to newer mesa stack. The newer mesa stack in 16.04 is 12.0.6

you could just use this ppa for latest stable mesa on 16.04
[https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates](https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates)

---

### Post by lumaja2 on 2017-04-13
Apologize for my mistake. Follow you suggestion found this:  sudo add-apt-repository ppa:ubuntu-x-swat/updates sudo apt-get update I want to be careful of this and need your help, is this the ppa your suggested?

---

### Post by mc4man on 2017-04-13
> **lumaja2 said:**
> Apologize for my mistake. Follow you suggestion found this:  sudo add-apt-repository ppa:ubuntu-x-swat/updates sudo apt-get update I want to be careful of this and need your help, is this the ppa your suggested?
yep, that ppa should work out fine. It's maintained by same person who handles mesa packaging for Debian & Ubuntu

---

