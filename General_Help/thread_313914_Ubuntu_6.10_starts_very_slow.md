---
title: "Ubuntu 6.10 starts very slow"
date: 2006-12-06
forum: General Help
---

### Post by kracheck on 2006-12-06
my ubuntu 6.10 starts very slow because during start-up it is trying to connect to the internet via my wireless card.  It can't however not automatically because it's a wpa network and i need to issue the command "sudo wpa_suplicant -Bw -Dwext -i eth1 -c/etc/wpa_supplicant.conf" as a script or in a terminal window.

Once i've issue this command all goes at a very normal and fast pace again.

What can I do about this ?

---

### Post by ingo on 2006-12-08
Hi,

number of things. Your network interfaces and their behaviour are determined by what is written in /etc/network/interfaces

I have configured mine so that my laptop automatically logs into my home wlan which runs on wpa. I suggest you search the forum for your particular card. 

If you are not sure about your wlan card do "lshw" (list hardware) and you should get a decent description.

HTH

PS.: I uncommented all non-active interfaces from my /etc/network/interfaces and boot up noticeably faster...

---

### Post by kracheck on 2006-12-08
hi there,

I found the solution :

I created the following script :
#! /bin/sh
# /etc/init.d/ActivateWpa
wpa_supplicant -Bw -Dwext -i eth1 -c/etc/wpa_supplicant.conf

Made it executable
Dropped it in /etc/init.d
In /etc/init.d no need to put any sudo in front of it since it runs as root on boot.

Made a symbolic link to cause the script to be executed when the system boots by issuing the following command in a terminal window :
sudo update-rc.d ActivateWpa defaults


Rebooted and off it went.  Wireless with Wpa_supplicant, wpa_supplicant.conf and a static ip adress.

---

### Post by ingo on 2006-12-09
well, trust someone else to come up with a different, but working, solution! linux is great, innit!

---

### Post by kracheck on 2006-12-09
It most certainly is.  It has a steep learning curve but persistance gets you there. Thanks for your help Belgium !

---

### Post by ingo on 2006-12-09
Belgium? Well, they brew excellent beer there, too. I consider it a compliment :)

---

