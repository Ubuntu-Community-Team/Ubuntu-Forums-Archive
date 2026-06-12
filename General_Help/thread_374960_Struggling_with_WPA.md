---
title: "Struggling with WPA"
date: 2007-03-03
forum: General Help
---

### Post by The Judderman on 2007-03-03
Hello all,

I have recently reinstalled ubuntu, upgrading to Edgy, and at the same time, upgraded my wireless security to WPA. I don't seem to be able to connect to WPA at all. I used ndiswrapper, which is working well, and the various wireless networks are detected, however, it still is not possible to connect to WPA. I tried this guide: [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html) , which made no difference at all... With Network Manager, all that happens, is that the applet turns over a few times, then reverts back to wired connection... Any ideas?

Cheers, 

The Judderman

---

### Post by The Judderman on 2007-03-03
Any Help?

---

### Post by petermck on 2007-03-09
I had similar problems trying to get network-manager-gnome working. Eventually I found a link on the Feisty forum which suggested commenting out all the entries in /etc/network/interfaces except lo. As in...
```
auto lo
iface lo inet loopback

# auto eth0
# iface eth0 inet dhcp

# auto ath0
# iface ath0 inet dhcp
# wpa-driver madwifi
# wpa-conf /etc/wifi.conf

# iface ppp0 inet ppp
# provider ppp0

# auto ppp0
```
All of a sudden (after a restart) nm-applet works well. 
Taking a step or two back, I installed wpasupplicant and edited a new file /etc/wifi.conf with the relevant setings based on the wpa-psk-tkip.conf example in /usr/share/doc/wpasupplicant/examples. Then I followed the instructions outlined in readme.modes in  /usr/share/doc/wpasupplicant and edited /etc/network/interfaces to what you see above and could connect, but it was messy. It seemed like wpasupplicant (and the debian.mode readme), Network Manager and Network-Manager-Gnome all had their own ideas about how to do things. Everything seems to work much better now with all the interfaces commented out except lo, which leads me to believe that now, network-manager-gnome is handling it all and doing a pretty good job.
The other thing that is needed is pam-keyring if you don't want password/passphrase hasseles. Thats explained at the WiFi HowTo [HTML]https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29[/HTML].
Hope this helps.:)

---

