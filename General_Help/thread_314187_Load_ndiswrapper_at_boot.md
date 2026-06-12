---
title: "Load ndiswrapper at boot"
date: 2006-12-07
forum: General Help
---

### Post by nasosp on 2006-12-07
I know that this question has been probably asked, but I REALLY couldn't find the answer in the forum. I am running Ubuntu 6.10 and every time I boot I need to type 3 commands to have my wireless network on so this is my question to you:

How can I load these commands automatically every time I boot?

$ sudo modprobe ndiswrapper
$ sudo iwconfig wlan0 essid MYESSID
$ sudo dhclient wlan0

P.S: Please help... I am so f***ing tired of writing them all the time :D

---

### Post by Stinger on 2006-12-07
To load the module at boot time , add "ndiswrapper" to your /etc/modules file ,
```
sudo gedit /etc/modules
```

remember to save the file ,as an example here is my /etc/modules file.
> 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper

8)

---

### Post by nasosp on 2006-12-07
Unfortunately this thing doesn't seem to work, I still need to do the same thing. Anyway I am not sure but I think things have changed in Ubuntu 6.10 (Edgy Eft )for modules? Haven't they?

---

### Post by Titus A Duxass on 2006-12-07
Now that you have ndiswrapper in /etc/modules add the other data to your /etc/network/intefaces file.

---

### Post by nasosp on 2006-12-07
Do you mean these 2 lines?

sudo iwconfig wlan0 essid MYESSID
sudo dhclient wlan0

---

### Post by Titus A Duxass on 2006-12-07
Not quite like that, do a search for an example.

You have the possibility to load up your specific data.

auto wlan0
iface wlan0 inet dhcp
wireless-essid YOURESSID

These are some of the lines.

---

