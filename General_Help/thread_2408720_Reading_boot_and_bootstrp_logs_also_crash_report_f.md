---
title: "Reading boot and bootstrp logs also crash report files"
date: 2018-12-21
forum: General Help
---

### Post by l6griffin on 2018-12-21
I'm trying to figure out why my installs a failing with too many errors. In doing so I started looking at boot and bootstrap log files. The bootstrap file tells me that libc6 was not installed. I tried to install it with apt-get and it failed too many errors. There is also a crash files in /var/crash I would like to read one is 16.1mb. I don't remember how to create a link to them. This is on a Dell Precision 2530 upgraded 16.04 to 18.04 LTS.

Larry

---

### Post by corradoventu on 2018-12-22
to see .crash files you need be authorized: ```
sudo adduser xxxx whoopsie
``` where xxxx is your user name

---

### Post by l6griffin on 2018-12-22
Thanks corradoventu, that added my name to the whoopsie group(?) and read up on whoopsie for additional information.

---

### Post by l6griffin on 2018-12-23
The solution was something of an anticlimax. I fooled around with liveusb trying to find a way to fix the file system and did multiple searches no luck. Finally a search had the answer 'disks'. Click on Activities type in disks, it allowed me to check the partitions, found the OS partition (sd3) was bad, then created an image, repaired sd3 in a tenth of the time to make the image. I'm thinking it couldn't be so I installed Polarr and no problem, no errors, can't be. I'll cross my fingers for a while anyway. I'll mark this solved.

---

