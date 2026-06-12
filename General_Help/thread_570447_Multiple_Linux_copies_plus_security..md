---
title: "Multiple Linux copies plus security."
date: 2007-10-08
forum: General Help
---

### Post by alzaf on 2007-10-08
I am concerned about security and I think it is complacent to say that Linux is 100% secure as there is a lot of software on top of the Linux Kernel that could potentially have vulnerabilities. 

My main use of my laptop is to browse the internet for favourite sites as well as online shopping and checking email. I would like to get my laptop as secure as humanely possible when doing these.

I think a way to do that is to have a partition with Linux on it that has as little software and services installed as possible for browsing the internet and another partition with Linux installed with other software I use like multimedia and occasional dabbling in programming.

I have a few questions to ask before I even contemplate thinking about carrying it out.

Does Grub automatically detect multiple partitions of Linux or would I have to configure it automatically?

In my browser-only partition, I must to keep everything as simple as possible. I would need a basic X-server so I can start Firefox and Thunderbird. Is there any way of doing this without having to install Ubuntu and removing all un-necessary software?

What services and daemons do I not require to have a Linux installation in the brower-only partition?

---

### Post by thirddeep on 2007-10-08
I recommend you put SElinux on for a start, and then read into samhein ([http://www.la-samhna.de/samhain/](http://www.la-samhna.de/samhain/)) & remote logging.  After that you want to encrypt your home file system : [https://help.ubuntu.com/community/FolderEncryption](https://help.ubuntu.com/community/FolderEncryption)

Then, instead of different partitions, use virtual machines (XEN/VMware/KVM).

Paranoia never has an end :-)

Thd.

---

### Post by crawdaddyangry on 2007-10-08
Hi

You might also consider simply booting from CD Ubuntu and a number of other distributions run very well in this fashion.

---

### Post by Naatan on 2007-10-08
if your main concern is security, use a BSD :p

---

### Post by alzaf on 2007-10-08
Thanks to all who replied so quickly, much appreciated.

I did think about virtualization but I'm concerned about the response times. I've never tried on Linux but I found it slow when I used it on Win XP in at work. It also goes against the 'strategy' I am aiming at which is to be more secure by having less software applications.

Again, the live CD is not an option due to response times. It's far too slow. 

As there is a number of options to take like file encryption, maybe Linux on a USB stick or the feasibility of virtualization.

---

