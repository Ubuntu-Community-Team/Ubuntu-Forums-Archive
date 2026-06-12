---
title: "ChrUbuntu Question - Partition Help"
date: 2013-08-30
forum: General Help
---

### Post by al10 on 2013-08-30
Hi, I'm new to Ubuntu and have recently installed ChrUbuntu on my Acer C710-2847 Chromebook.

I've setup aliases to switch between ChrUbuntu and the stock Chrome OS. The first time I performed the switch I could switch between the two OS's with ease, however I am no longer able to boot into the Chrome OS. I have a basic knowledge of the cgpt command which I used to setup the aliases, however I have no knowledge of the partition table that was created or what the individual partitions are for.

I would greatly appreciate any help of determining what each partition is and it's function (whether related to ChrUbuntu or Chrome OS)

Here's a screenshot of the partition table using the 'sudo parted -l' command

I also have a screenshot of the ChrUbuntu info.

The command I've setup to switch between OS's is

Switch to Chrome => alias chromeos='sudo cgpt add -i 6 -P 0 -S 1 /dev/sda; sudo reboot'

Switch to Ubuntu => alias ubuntu='sudo cgpt add -i 6 -P 5 -S 1 /dev/sda; sudo reboot'

---

