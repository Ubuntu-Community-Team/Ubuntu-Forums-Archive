---
title: "Wireless stoped working when upgraded to 8.04"
date: 2008-05-01
forum: General Help
---

### Post by idipous on 2008-05-01
I had 7.04 and it recognised my usb wireless card (Linksys wusb54g) straight away upon install. Even though I could not use roaming mode when I gave fixed ip it worked just fine. Since 7.10 and now with 8.04 although the card is recognised I cannot seem to connect neither to my router nor to the internet (ofcourse). The driver 8.04 installs is the rt2500usb and network manager recognises my ESSID "linksys". If I get my pc next to my router I can connect to the internet wirelessly with no problem (using either roaming mode  or fixed ips).

When I get the pc to my room (where 7.04 and windows as well as OS X have connectivity) it seems that it cannot connect. What was it that changed from 7.04? I think that the drivers were the same. If not which one was there and how can I uninstall the current driver to install the old one? 

Thanks in advance for any help
idipous

---

### Post by cmnorton on 2008-05-01
Is Network Manager running?

Backup your /etc/network/interfaces file, and then edit it to look like this.

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

I am assuming you are getting DHCP addresses from your wireless router.

Reboot, and then see if you can connect.

If you were to look at your "manual" configuration option in Network Manager or System -> Administration -> Networks, your interfaces should all be set to roaming.

This is all from direct experience going from 6.06 to 6.10 to 7.04. I did not have this problem going from 7.04 to 7.10. I think your network interfaces worked fine, but were set to non-roaming back in 7.04. This does not mean you cannot have non-roaming interfaces; it is just how I got wireless networking and vpn going over the wireless networking to work.

---

### Post by idipous on 2008-05-02
Thanks for the reply. 

The /etc/network/interfaces is already as you describe. Furthermore, I have to say that when I put the pc next to the router it connects perfectly. The problem is when I get far from the router (in this case I have internet only with windows and Mac OS X -and with 7.04 when I had it installed).

---

### Post by cmnorton on 2008-05-02
> **idipous said:**
> Thanks for the reply. 

The /etc/network/interfaces is already as you describe. Furthermore, I have to say that when I put the pc next to the router it connects perfectly. The problem is when I get far from the router (in this case I have internet only with windows and Mac OS X -and with 7.04 when I had it installed).

I have an older Acer Laptop (Travelmate 630) . It has a built-in Atheros wireless card. It connects poorly, even sitting next to the router. I use a Cardbus Linksys card, and the connection is better. The Atheros card would not support vpn connections well at all.

---

### Post by idipous on 2008-05-02
So it is my linksys card? But why does it connect with windows and 7.04. It is a desktop pc and the card is a Linksys wusb54g. I will try use ndiswrapper but first I should uninstall rt2500usb. Can you suggest how to do uninstall this driver as i have never done such a thing before?

---

### Post by cmnorton on 2008-05-03
My linksys card just worked with installed Linux drivers. Do you have to use ndiswrapper? The LinkSys seem to work without much tweaking on two systems I have.

---

### Post by idipous on 2008-05-03
The same card did work perfectly on 7.04. I just installed 8.04 and it doesn't. I don't know what else to do. I would prefer using a proper open source driver but it does not work so I have to search for an alternative. 

Now in order to install ndiswrapper do I have to blacklist the current driver?

---

### Post by idipous on 2008-05-18
Problem Solved!!!!

I am writing this as a reference to people having the same problems as I had. My problem was this. I had a Linskys usb wireless card (WUSB54G v. 4) that although it worked under 7.04 it did not in 7.10 and 8.04 (of Kubuntu 8.04). 

The solution to my problem was the following: 

I had to remove the module Ubuntu 8.04 installed by default and install rt2570 driver.

download the driver from here: [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz) 

and then

```

$tar xvzf rt2570-cvs-daily.tar.gz
$ cd rt2570-cvs-***/Module
$ sudo make install
$ sudo modprobe rt2570
$ sudo modprobe -r rt2500usb

```

And the device will stop been recognized as wlan0 but as rausb0 (as it was in 7.04).

Now although dhcp and (probably roaming mode) does not work (it did not work for me in 7.04 either) if you make a manual ip set up it works!

I would like to say that great help was found in this post [http://ubuntuforums.org/showthread.php?t=580448&page=5](http://ubuntuforums.org/showthread.php?t=580448&page=5) from the reply of robjoski.

Good Luck to everyone.

---

