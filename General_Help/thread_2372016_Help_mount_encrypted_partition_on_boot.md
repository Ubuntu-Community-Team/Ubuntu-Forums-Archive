---
title: "Help mount encrypted partition on boot"
date: 2017-09-20
forum: General Help
---

### Post by cyberfarer on 2017-09-20
Hello

I have set up an encrypted partition on a notebook. I can easily mount the partition in the correct space with the command:
cryptsetup luksOpen /dev/sda5 data

The problem I am having is I want the partition to mount on boot. During the boot process, I see the prompt to enter the passphrase but there is no pause to allow me to do so. It just flies right past.

I have Googled for an answer but can't find one. It strikes me that this should be pretty basic and not that hard and yet I am completely stumped and frustrated. 

If anyone can offer any insight I will be forever grateful.

Thank you.

---

### Post by lister171254 on 2017-09-20
Have a look at this
[https://evilshit.wordpress.com/2012/10/22/how-to-mount-a-luks-encrypted-partition-on-boot/](https://evilshit.wordpress.com/2012/10/22/how-to-mount-a-luks-encrypted-partition-on-boot/)

Good luck

---

### Post by cyberfarer on 2017-09-20
Thank you for the reply. I followed that and the issue persists. I can see the passphrase prompt scrolling by at a high rate of speed. It just doesn't stop.

---

### Post by Mark_in_Hollywood on 2017-09-20
First, I'm not good at ecrypt, but maybe this?

[http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)

---

### Post by lister171254 on 2017-09-24
Can you post the content of /etc/crypttab & /etc/fstab

---

