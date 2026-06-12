---
title: "rmmod and insmod"
date: 2007-09-06
forum: General Help
---

### Post by Sqwishy on 2007-09-06
I got a new video card and had to get new drivers and compiled the nvidia kernel api or something, anyway. whenever i start the box, gdm doesn't load because it's using the wrong api version right. so i log into a terminal and run the following

cd /lib/modules/2.6.20-16-generic/kernel/drivers/video #to the modules
sudo rmmod nvidia.ko #to get rid of the old version
sudo insmod nvidia.ko #to use the newer version (in the folder i cded to)

and i hafta do that every bootup, and i've done it before, but i forgot how to get it so it automatically loads the correct version thingy when it boots up. help?

---

