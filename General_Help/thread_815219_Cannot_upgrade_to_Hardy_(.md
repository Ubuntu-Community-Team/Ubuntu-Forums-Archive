---
title: "Cannot upgrade to Hardy :("
date: 2008-06-01
forum: General Help
---

### Post by GCoffee on 2008-06-01
Hello,

I am having a problem upgrading to hardy. 

Whenever I try to upgrade using the distro update thing it gets to setting software channels, does some of it, then stops saying it is unable to continue saying this error could be caused by upgrading to a pre-release version of ubuntu, using a pre-release version of ubuntu. ETC

I have installed all current updates,
Please help!

Cheers.
GCoffee.

---

### Post by GCoffee on 2008-06-01
bump

---

### Post by dr.koljan on 2008-06-01
Have you added any third-party repositories? (Wine, Medibuntu, Skype etc)

---

### Post by GCoffee on 2008-06-01
The third party repostries are not enabled, I haven't added any repostries and I haven't installed any software..

---

### Post by Amarsingh0793 on 2008-06-01
Try this in a terminal:

sudo apt-get dist-upgrade

---

### Post by GCoffee on 2008-06-01
readout from terminal:

jack@jack-desktop:~$ sudo apt-get dist-upgrade
[sudo] password for jack:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jack@jack-desktop:~$ 
jack@jack-desktop:~$ 

BTW, my username isn't actually jack.

Cheers,
GCoffee.

---

### Post by sailor2001 on 2008-06-01
it's often suggested to do a clean install rather than an upgrade. Download Hardy from "torrent ubuntu" and burn to disk at a slow speed and install from that

---

### Post by GCoffee on 2008-06-01
Any reason why to burn disc at slow speed?

---

### Post by buntunub on 2008-06-01
> **GCoffee said:**
> readout from terminal:

jack@jack-desktop:~$ sudo apt-get dist-upgrade
[sudo] password for jack:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jack@jack-desktop:~$ 
jack@jack-desktop:~$ 

BTW, my username isn't actually jack.

Cheers,
GCoffee.

Nice. Welcome to Hardy! Your upgrade is done it seems.

---

