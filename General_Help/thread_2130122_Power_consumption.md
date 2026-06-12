---
title: "Power consumption"
date: 2013-03-28
forum: General Help
---

### Post by avsksan on 2013-03-28
Hello Everybody,
                          Recently i have installed Ubuntu 12.04 LTS in my laptop (ACER ASPIRE E1-571G) It seems that the system gets hot when compared to Using Windows 7. And the battery get down more quickly. Is that Ubuntu consumes lot more power than Windows?

---

### Post by 3rdalbum on 2013-03-28
Are you using the Nvidia driver provided by the Additional Drivers program?

Also, are there any programs constantly running at 10% CPU or higher? System Monitor will allow you to monitor the amount your CPU is working.

---

### Post by avsksan on 2013-04-01
I have a Nvidia card but i have not installed any graphics Driver. Do i need to install one. is that the problem i have. By the way i have no program running for CPU usage greater than 10 %. REPLY.

---

### Post by xianbei on 2013-04-01
jupiter is a good program for battery saving:

sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter

---

### Post by Linuxisfast on 2013-04-01
I would recommend TLP over Jupiter, its far more comprehensive and effective and I have used Jupiter in the past. The TLP actually lowers power consumption. Also make sure to add x-swat ppa to get latest nvidia drivers and enable them, they lower power consumption. Also install Bumblebee to switch between intel graphics and nvidia. TLP can be found at [www.linrunner.de](www.linrunner.de)

---

