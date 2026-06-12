---
title: "new 1060plus tablet not responding"
date: 2018-06-03
forum: General Help
---

### Post by thefoxhacker2004 on 2018-06-03
Hi, I'm a 14 year old Linux user.
 i just buy a new1060plus huion graphical tablet:o:D

i fallow these instruction:
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install git
git clone [https://github.com/kolrabi/digimend-kernel-drivers.git](https://github.com/kolrabi/digimend-kernel-drivers.git)
cd digimend-kernel-drivers
make
sudo rmmod hid-kye
sudo rmmod hid-uclogic
sudo rmmod hid-huion
sudo make uninstall
sudo make install

than i reboot.
the tablet pen work perfectly with my debian strech-workstation.:cool:
 but i have no response with my Lubuntu 18.04- Latitude 2120.:-k:cry:

I taugh it is because my memory is full of application. 
For that, i re install lubuntu on my latitude and repeat the same instructions.
it doesn't work](*,)

can some one help me please?
tanks in advance to help me, i really appreciate!

ps:I from quebec city, my english is not really good.8-[

---

### Post by Perfect Storm on 2018-06-04
Moved to General forum.

---

### Post by mörgæs on 2018-06-17
If original poster is still here:

Please post the link where you found the instructions. Also please post (in CODE tags) the output from each of the commands.

---

