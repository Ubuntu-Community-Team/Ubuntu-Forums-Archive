---
title: "My wireless stopped working since I update ubuntu"
date: 2007-02-22
forum: General Help
---

### Post by pearlygate on 2007-02-22
Please help, my wireless card stopped working since I updated my ubuntu last night. 
I'm using Dell Inspiron 6400 with broadcom 1390 wireless card. It worked perfectly before.

Btw, I installed the driver in conjunction with ndiswrapper stuff (followed all the steps from here: [http://www.ubuntuforums.org/showthread.php?t=297092](http://www.ubuntuforums.org/showthread.php?t=297092) )

here is the iwlist scanning result:
> 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

somehow eth1 is not detected. In addition, the wifi LED is not turned on. 

here's the iwconfig
> 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

here's the /etc/network/interfaces
> 
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



auto eth0

iface eth1 inet dhcp
wireless-essid airseas



auto eth1


please help

---

### Post by teaker1s on 2007-02-22
others complaining of this try installing
ndiswrapper-utils-1.9
failing that look at this thread, maybe someone has answer
[http://www.ubuntuforums.org/showthread.php?t=358004]("http://www.ubuntuforums.org/showthread.php?t=358004")

---

### Post by pearlygate on 2007-02-22
So I'm not the only one. I'll look into this. Thanks a lot :)

---

