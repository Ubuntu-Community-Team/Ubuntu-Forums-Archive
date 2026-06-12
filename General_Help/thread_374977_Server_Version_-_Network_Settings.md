---
title: "Server Version - Network Settings"
date: 2007-03-03
forum: General Help
---

### Post by Sjoram on 2007-03-03
Hi all

Relatively new to Linux, reinstalled with server version to get LAMP/DNS server easier.  Want to run GNOME GUI until I'm happier working in terminal, but at install I did not configure the network settings, so can't run sudo apt-get update

Trying to find out the commands to use in terminal to manually set up my network settings?

Thanks! :)

---

### Post by Bite_me_Bill on 2007-03-03
You need to edit the interfaces file first.
sudo nano /etc/network/interfaces

then restart networking.

---

### Post by Sjoram on 2007-03-03
> **Bite_me_Bill said:**
> You need to edit the interfaces file first.
sudo nano /etc/network/interfaces

then restart networking.

I managed to "view" it, but not too sure how to edit it/what to add to it

---

### Post by zvacet on 2007-03-03
**Read this**
system>help>system documentation>Ubuntu server guide>networking

---

### Post by cookfromfrozen on 2007-03-03
Try this if you use DHCP:

```
sudo ifconfig eth0 up
sudo dhclient eth0
```

...or if you're static, edit your /etc/network/interfaces file  (sudo nano /etc/network/interfaces) and adapt the eth0 section to look something like this, here's mine:

```

iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
auto eth0

```

Then run

```
sudo /etc/init.d/networking restart
```

to restart the network interface

---

### Post by Sjoram on 2007-03-03
Manged it, Thanks for the replies.  When I checked the config files, all was set as it should have been. However I have two NICs in my machine, recognised as eth0 and eth1. The one I thought was eth0 was actually eth1! When I swapped the cable to the other NIC, all was fine! :oops: :oops: :oops:

---

