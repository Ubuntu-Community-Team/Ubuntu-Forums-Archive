---
title: "Grub has stopped giving choice to boot from my main HD"
date: 2020-12-06
forum: General Help
---

### Post by ra7411 on 2020-12-06
I have 2 hd's on this machine, both running 18.04.

The main hd is a 500gb ssd, which shows up fine on Disks as sda1 which is the main o/s I use, and sda2 /home.

The other hd is a 4tb spin drive with aux o/s  sdb1.

Grub has stopped showing sda1 as a choice, I only get the aux choice sdb1.

I've tried boot repair several times with no success.  

(   $ sudo add-apt-repository ppa:yannubuntu/boot-repair
$ sudo apt update
$ sudo apt install boot-repair
$ sudo boot-repair   )

Attached is some output, I tried using the code approach but I didn't have a "security token"???

added:   here's the paste bin address from boot repair:

[http://paste.ubuntu.com/p/TvbfYnrzkj/](http://paste.ubuntu.com/p/TvbfYnrzkj/)

---

