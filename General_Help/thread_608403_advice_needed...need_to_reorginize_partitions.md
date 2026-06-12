---
title: "advice needed...need to reorginize partitions"
date: 2007-11-10
forum: General Help
---

### Post by zeltak on 2007-11-10
Hi all

i need some advice for you guys. i have a 500gb drive which i just go with my new comp a few weeks ago. I  installed windows (sda1) and then kubuntu (sda2) and made /home a separate partition (sda3). I then decided to try ubuntu and installed it (now sda4). In the install process i couldnt create a swap file (i didnt know at the time about the whole extended/logical thing) so i ended out without a swap drive (i get by with my 4 GB RAM :)...). I did leave about a 1 GB of space in the installation which i have no Idea where it is on the drive now.

I do want to create a swap drive so the following questions arise (since i dont want to screw up my whole drive)

1) whats the best way to proceed in order to create a swap drive in my situation
2)the grub boots from sda4 (ubuntu) which i dont use as my main Desktop. I rather use Kubuntu  (sda2). is there a way to move the /boot/grub/menulst to sda2?

thx alot in advance

Zeltak

---

### Post by overdrank on 2007-11-10
> **zeltak said:**
> Hi all

i need some advice for you guys. i have a 500gb drive which i just go with my new comp a few weeks ago. I  installed windows (sda1) and then kubuntu (sda2) and made /home a separate partition (sda3). I then decided to try ubuntu and installed it (now sda4). In the install process i couldnt create a swap file (i didnt know at the time about the whole extended/logical thing) so i ended out without a swap drive (i get by with my 4 GB RAM :)...). I did leave about a 1 GB of space in the installation which i have no Idea where it is on the drive now.

I do want to create a swap drive so the following questions arise (since i dont want to screw up my whole drive)

1) whats the best way to proceed in order to create a swap drive in my situation
2)the grub boots from sda4 (ubuntu) which i dont use as my main Desktop. I rather use Kubuntu  (sda2). is there a way to move the /boot/grub/menulst to sda2?

thx alot in advance

Zeltak

HI maybe this link will help it worked for me
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

