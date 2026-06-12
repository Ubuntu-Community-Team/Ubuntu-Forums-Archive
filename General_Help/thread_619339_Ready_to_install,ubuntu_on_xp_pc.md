---
title: "Ready to install,ubuntu on xp pc"
date: 2007-11-21
forum: General Help
---

### Post by nikef on 2007-11-21
Hi all
i have a fujitsu siemens computer,with windowze xp,service pack 2
i am ready to install ubuntu gutsy gibbon 7.10 on it :)
i would like to keep windows for other members of the family,i am still a newby to linux,i have installed  it on my older pc
i would like to know,i have a wireless keyboard and mouse,so shall i do the install with those hooked up to my pc,or shall i just add my old ps2 keyboard and mouse and then deal with the wireless keyboard and mouse after install.

thanks  :)

---

### Post by scrooge_74 on 2007-11-21
You will install no problem and work in a dual boot enviroment.

When installing you need to make a manual set up of the partitions to make room for ubuntu.

those are usb if I am not mistaken.  You can go ahead and use the old ones. And when you have the system setup reboot with the wireless ones connected

---

### Post by skyjacker on 2007-11-21
Be sure you defragment the hard drive several times prior to partitioning the drive for ubuntu.

---

### Post by nikef on 2007-11-21
> **skyjacker said:**
> Be sure you defragment the hard drive several times prior to partitioning the drive for ubuntu.

Hi,only just read your message,i only defragmented windows once

i have finnished the install,and updated ubuntu,and also started windows xp,everything seems to be ok,on start up,i get an out of range on my monitor,but it carrys on and boots up ok 

thanks for your help :)

---

### Post by nikef on 2007-11-21
> **scrooge_74 said:**
> You will install no problem and work in a dual boot enviroment.

When installing you need to make a manual set up of the partitions to make room for ubuntu.

those are usb if I am not mistaken.  You can go ahead and use the old ones. And when you have the system setup reboot with the wireless ones connected

thanks for your help,i restarted my pc,with the wireless keyboard and mouse,it works great while in ubuntu,but at start up,if i want to move down the list to start windows,my wireless keyboard will not work :confused:

---

### Post by Bablefish on 2007-11-21
Try this I have heard good things about it.

[https://launchpad.net/lubi](https://launchpad.net/lubi)

---

### Post by scrooge_74 on 2007-11-21
Remember the wireless driver comes in after the kernel boots, grub is before that

---

### Post by hikaricore on 2007-11-21
> **scrooge_74 said:**
> Remember the wireless driver comes in after the kernel boots, grub is before that


errr.... wireless keyboard should work fine as long as bios is reading the usb connections before grub starts.  Most modern bios do just this, but if it's not working check your bios settings or test another usb port incase something is flakey (example my mb only reads the front usb ports for key/mouse before booting into grub O.o)

---

