---
title: "Bizarre network problem with edgy."
date: 2007-02-18
forum: General Help
---

### Post by Lateralus@desktop on 2007-02-18
Ok. So I'm using Dapper right now, straight off the Live-Cd, and networking works fine. It also works amazingly when I have it installed. However, when I install Edgy, it refuses to work. 

I have a RT2500 802.11b/g wireless card, which connects to a Belkin G+ MI/MO Router. As I said, it works perfectly with Dapper, but doesnt work in Edgy. 

In Dapper, it lets me get away with not entering an ESSID or network password. I can then activiate it, and it works perfectly. 

In Edgy, I click on 'enable this device' and change the connection to automatic DCHP, and it refuses to work because I didnt enter an ESSID.

If anyone can please help, that would be greatly apreciated.

---

### Post by g8m on 2007-02-18
I ended up editing /etc/network/interfaces. And filling in the info there.
  iface eth1 inet static
  address 192.168.0.2
  netmask 255.255.255.0
  gateway 192.168.0.1
  wireless-essid aquarius
  pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
  post-down killall -q wpa_supplicant


But I am using static adresses, no dhcp. And I configured wpa_suppicant to use wpa key.

---

### Post by Lateralus@desktop on 2007-02-18
This is all thats in my interfaces file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ra0 inet dhcp

auto ra0

Which I was going to just copy into the one in Edgy, but I doubt that will work...

---

### Post by g8m on 2007-02-18
Entering "iwconfig" in a terminal will tell you wich interface has wireless extensions.

Copying probably doesnt work, dont know what ip your gateway has.

---

### Post by Lateralus@desktop on 2007-02-18
iwconfig actually gave me the ESSID my wireless is using right now, so that should mean, if I type that when I use Edgy, it should work, right?

---

### Post by g8m on 2007-02-19
If iwconfig tells you the ssid, the interface is already configured for that ap.  Do you get an ip from the ap? (type ifconfig in a terminal). If it's not up type "sudo ifconfig "interface" up", where interface is your wireless interface, for example eth1.

---

