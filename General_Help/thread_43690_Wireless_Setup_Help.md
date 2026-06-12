---
title: "Wireless Setup Help"
date: 2005-06-22
forum: General Help
---

### Post by Epithett on 2005-06-22
I have a huge favor to ask of anyone who is willing to help me. I need to install my Linksys Wireless Internet adapter into my Ubuntu PC but I have no idea how. I have read many topics and have the directions, but as I am grand spankin' new to Linux, I have no idea what it is asking of me. If anyone is willing to give me their AIM screen name and help me, I would be ever so grateful. If not, any help would be nice. What I need to do is:
> 1) Add 'wireless_mode managed" before setting essid in the interfaces file.

2) put the prefix s: to the wireless key.  What your interfaces should resemble:
iface wlan0 inet dhcp
name Wireless LAN card
wireless_mode managed
wireless_essid myessid
wireless_key s:mynetworkkey

wireless_channel 11
auto wlan0
My problem is, I have no idea where to start!

---

### Post by sfw5000 on 2005-06-22
Just for a little background -- I assume you already installed the card and booted up and ubuntu did not successfully find the card? And you went through the GUI to try to set it up?

If not, do that (System-->Administration-->Networking)

If so, the file that quote is talking about is /etc/network/interfaces. Mine is below. To open it type

```
sudo gedit /etc/network/interfaces
``` 

```

# The primary network interface
iface ath0 inet static
        address 192.168.0.157
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid larry
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1

auto ath0

``` 

Note that yours might be called "wlan0" instead of "ath0"

Also note that the entire file was generated automatically and I didn't have to do anything -- the GUI does it all.

---

