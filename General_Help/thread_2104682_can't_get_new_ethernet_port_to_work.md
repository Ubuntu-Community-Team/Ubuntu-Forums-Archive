---
title: "can't get new ethernet port to work"
date: 2013-01-13
forum: General Help
---

### Post by garyed on 2013-01-13
Running 10.04 on an all in one Foxconn MB. Things have worked fine for a couple years & now I'm pretty sure the built in ethernet port has gone bad. My ifconfig shows "0"  RX or TX bytes so I decided to install a pci ethernet card I had laying around. I think the card is working fine because it shows about 75 to 100k RX & TX bytes. The card shows up as eth2 but I can't figure how to set my system up to use eth2. It always used eth0 as default.
 Any help appreciated.

---

### Post by d4rk0wl on 2013-01-14
Well it is good the operating system reconises it automaticaly. You will probably need to edit
```
/etc/network/interfaces
```

If you want to use DHCP add something like this:
```

auto eth1
iface eth1 inet dhcp

```

Or if you would like to make it a static IP, use:
```

auto eth1
iface eth1 inet static
address 192.168.1.50
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

Or change that to what ever you like, after that run:
```
sudo service networking restart
```
Let me know how that turns out. :)

Regards,
- D4rk0wl

---

### Post by garyed on 2013-01-14
Actually I already edited the /etc/network/interfaces file but I still can't connect. All I did was replace all the instances of eth0 with eth2 which is the new pci ethernet card. I rebooted several times but it still doesn't work though it looks like eth2 is working when I run ifconfig.

---

### Post by rnerwein on 2013-01-14
> **garyed said:**
> Actually I already edited the /etc/network/interfaces file but I still can't connect. All I did was replace all the instances of eth0 with eth2 which is the new pci ethernet card. I rebooted several times but it still doesn't work though it looks like eth2 is working when I run ifconfig.
hi
it looks like you have configured your first interface with the NetworkManager.
have a look at: /etc/NetworkManager/NetworkManager.conf
there is an option: no-auto-default
may this will help you
good luck

---

### Post by garyed on 2013-01-14
Well I decided to use my other desktop that has always worked perfectly & see if I could find some kind of settings & after making some changes now I can't get on from 10.04 on that one either. I was trying to get a network icon on my top panel so I changed the line in /etc/Networking/nm-system-settings.conf "managed=false to managed=true" rebooted & no internet connection. I changed the file back & rebooted but still no internet connection. At least on this desktop I also have 12.04 installed, I can connect fine so I assume its all in the setup on both computers. The question is what are all the files & settings that are needed to connect to the internet. The only one I know of is:
/etc/network/interfaces

---

### Post by steeldriver on 2013-01-14
/etc/network/interfaces is the 'old style' way of doing things, it relates to a service called 'networking' e.g. 'service networking status'. This is the default on older installations and newer Ubuntu Server installations.

/etc/NetworkManager/NetworkManager.conf relates to a newer service called 'network-manager' that is better suited to roaming - that's the one that's controlled by default using the applet on the GUI. It is the default way of doing things for current Ubuntu Desktop editions. It allows easier user-level configuration which is useful for wifi / mobile devices.

Normally the GUI applet does not control any connections defined in the older 'networking' service (unless you set 'managed=true" for ifupdown, as you appear to have just done)

In most cases you should use one OR the other and not mix them - I would suggest reverting things to how they were and THEN we can troubleshoot why the new device is not working

---

### Post by garyed on 2013-01-14
Well I got it working but I still can't figure out why. 
What I did was made a copy of my /etc/network/interfaces file & then started a new one from scratch with just two lines:
> auto lo
iface lo inet loopback

Rebooted & everything worked fine.
Then I replaced the interfaces file with the one that I had that had a static ip address & it works fine too. 
I did the same thing with the other computer that had the original problem & all is well with that one also. The only thing I can figure is that the static ip setup was causing a problem initializing but once the dynamic ip was working then the static ip could work also. 
Thanks for all the ideas

---

