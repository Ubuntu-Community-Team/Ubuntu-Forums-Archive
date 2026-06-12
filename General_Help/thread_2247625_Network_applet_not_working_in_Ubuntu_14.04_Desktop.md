---
title: "Network applet not working in Ubuntu 14.04 Desktop"
date: 2014-10-09
forum: General Help
---

### Post by abcuser on 2014-10-09
Hi,
I would like to install Ubuntu 14.04 Desktop, but at the installation time I only have had "Ubuntu 14.04 Server". So I installed
"Ubuntu 14.04 Server" and after installation was finished I installed "ubuntu-desktop" package.

Now I have rebooted the machine and "Ubuntu Desktop" is up and running. The only think that is not working in "Ubuntu Desktop" is network indicator at the top-right beside clock.

Also if I click on Edit Connection from network applet (from top-right) and the list of network connections is empty. But I can just normaly access internet with Firefox browser. 

It looks to me that network settings between Ubuntu Server and Ubuntu Desktop are not defined in the same place. So my Ubuntu Desktop now recognizes settings that were defined at the time of pure Ubuntu Server install.

Is there a way to fix this network indicator - I would like to know if network is up or not and also to make it possible to define network connections using Ubuntu network indicator applet?

Thanks

---

### Post by nerdtron on 2014-10-09
Hhhhmmm if your problem is only to set the network IP address, either DHCP or static and to know if the network is up or down, you don't have to install a full blown GUI. You just have to edit the /etc/network/interfaces file and set the IP there.
Sample configuration.
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
 # The loopback network interface
auto lo
iface lo inet loopback
 # The primary network interface
auto eth0
 # DHCP not needed
# iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 8.8.8.8 
```

To activate the new settings after saving the file, run:
```
sudo ifdown eth0 && sudo ifup eth0 
```

Anyway if you still want to use the GUI, did you install the network manager package?
```


sudo apt-get install network-manager 
```

---

### Post by abcuser on 2014-10-10
> **nerdtron said:**
> Hhhhmmm if your problem is only to set the network IP address, either DHCP or static and to know if the network is up or down, you don't have to install a full blown GUI.
That was not the case. I wanted to have Ubuntu Desktop installed (so GUI), but at the time of installation I only had "Ubuntu Server" installation on my USB key and PC without operating system, so I was not able to download Ubuntu Desktop. So I installed Ubuntu Server and then install GUI on it (package ubuntu-desktop). According to many articles I have read Ubuntu Desktop is only GUI upgrade of "server" software, but it looks this isn't exactly like that, there are some little tweaks need to be done.

Now that I have GUI up and running (but broken network indicator), I have decided to download "Ubuntu 14.04 Desktop" and install it on this machine overriding old "Ubuntu 14.04 Server + GUI" installation, to be 100% sure I don't get into some strange problems no one else has. I intend to have this installation as long as possible, for example for 5 years until LTS expires the software update.

Thanks a lot for helping me out. Problem solved.

---

