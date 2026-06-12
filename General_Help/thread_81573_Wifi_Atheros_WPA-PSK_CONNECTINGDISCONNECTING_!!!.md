---
title: "Wifi Atheros WPA-PSK CONNECTING/DISCONNECTING !?!!?"
date: 2005-10-24
forum: General Help
---

### Post by Xenus98 on 2005-10-24
Hi All,
I'm using Ubuntu on a laptop. 
I use a DLINK DWL-G650 with static ip for more security.
I tested WEP Encrypted connection (out of the box after installation of ubuntu) and it work working OK.
I decided so to go on with WPA-PSK encryption.
Installed WPA_SUPPLICANT.
Configured.
But there cant understand what is hapenning, as I am starting wpa_supplicant, it scan, connect, get authorized... and after a few seconds... disconnect...and reconnect again...
I used wpa_cli to try to make some diag.
When I type 'status'. Everything is OK. That is quite crazy.

Anyone as an idea ?
Where to start from ?

---

### Post by janne5011 on 2005-10-24
[QUOTE=Xenus98]Hi All,
I'm using Ubuntu on a laptop. 
I use a DLINK DWL-G650 with static ip for more security.
I tested WEP Encrypted connection (out of the box after installation of ubuntu) and it work working OK.
I decided so to go on with WPA-PSK encryption.
Installed WPA_SUPPLICANT.
Configured.
But there cant understand what is hapenning, as I am starting wpa_supplicant, it scan, connect, get authorized... and after a few seconds... disconnect...and reconnect again...
I used wpa_cli to try to make some diag.
When I type 'status'. Everything is OK. That is quite crazy.

Anyone as an idea ?
Where to start from ?[/QUOTE]


hi if you later on when finish (if) the  wpa-psk set up you can write a complete guide for this?:smile: 
I think my card is the same (atheros 5212-chip right?)-
I can not find a good guide for this (for a linuxbeginner at least)
thanks
//Janne

---

### Post by Xenus98 on 2005-10-25
Janne, I may think about it, but if you have a look around, you will see in wiki and in the forum of ubuntu some already related guide  that are very helpful.
Read them, take the time to understand what all these things want... and try.. and retry... and you will make it work.

Tonight, I made it. My DLINK DWL-G650 is working in WPA-PSK as I am writing these lines ! I am also using Static IP, not DHCP like a lot of Guides are showing.
And for sure, this was not the more difficult.

So what I did ?
I cant tell which step was exactly missing to me but this is what I did tonight and that make me successful...

**1)** after a readme a guide I decided to use wpa_passphrase to encode my secret key instead of having it clearly written in my config file (/etc/wpa_supplicant.conf).

=> **wpa_passphrase your_SSID your_secret_passphrase_in_normal_text**

Ex : **wpa_passphrase HyperNetwork OpenTheDoor**

This command will generate a brief description of your network in WPA syntax.
The most important line to copy from is the "psk=..." with the Hex numbers.
This is the result of encoding your secret key.

**2)** Edit your /etc/wpa_supplicant.conf and modify the definition of your network, adding the newly generated psk secret key.

Here is a part of my wpa_supplicant.conf (network and psk key are fictif).
The line starting with a # are just a comment for reader and are not used by the config file.

....
[B]
#HERE START THE DEFINITION OF MY WIFI NETWORK....
network={
        ssid="HyperNetwork"
        proto=WPA
        scan_ssid=1
        key_mgmt=WPA-PSK
#       psk="OpenTheDoor"
        psk=38144375f57e9bdda07e97ab6a58c3f5cf794fc7d85a83fca95cc2b7
        pairwise=TKIP
        group=TKIP
}
[/B]
**3)** I also edited the file /etc/network/interfaces to remove any line refering to a WEP configuration previoulsy defined. I also fixed the static neetwork address of the interface. The network 11.2.3.0 is given here as an example. Replace these 3 number by your own local network values. If your AP is doing DNS forwarding, use it in the DNS list as a nameservers, if not, replace the IP by another DNS server.

....
[B]
iface ath0 inet static
        address 11.2.3.10
        netmask 255.255.255.0
        network 11.2.3.0
        broadcast 11.2.3.255
        gateway 11.2.3.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 11.2.3.1 66.249.93.99
[/B]

**4)** Run wpa_supplicant. There is a lot of post on how to do that.
You can run it in the background or in the foreground to help debugging.
That what I did. Example :
=>**wpa_supplicant -i ath0 -c /etc/wpa_supplicant.conf -D madwifi -w -d**
Option -d is for debug, you can start without it first even for simple messages.

to run it in the background, use option -B
=>**wpa_supplicant -B -i ath0 -c /etc/wpa_supplicant.conf -D madwifi -w**


**5)** Check that your wifi interface (ath0 for me) is up. If you like, put down other interface that you dont use.
To be sure the interface wifi is down (replace ath0 by the name of your wifi interface)
=> **ifdown ath0**
put it up now !
=> **ifup ath0**

and try to ping [www.google.com](www.google.com) or to surf !!!

Hope it did help anybody !!
Next step for me is to put all this to start at boot time ! :))
This should be not too difficult.
See you allll ! !! ! ! !

---

### Post by thinair on 2005-10-26
Same problem under 5.10, I think it's a bug related to the package wpa_supplicant or madwifi-driver (restricted kernel)
This was working fine under 5.04 !

---

### Post by Xenus98 on 2005-10-26
thinair :

Now everything is OK, I guesss a problem was coming from my non encoded WPA-PSK secret key.

---

### Post by Bil-E-daKid on 2005-10-26
Most likely a passphrase problem as you indicated.

I saw *exactly* this symptom on an XP Home machine in the weekend. (Constantly connecting, disconnecting etc).

Problem was I had put the wrong passphrase in. As soon as it was right, the connection came up and stayed there.

---

### Post by Xenus98 on 2005-10-26
Yes, it is apparently not the same to have a secret key in wpa_supplicant.conf in ascii then to have it encoded in hex. (via wpa_passphrase)

---

### Post by thinair on 2005-10-27
I do not test again, but my passphras is in hex

what about this bug report [http://bugzilla.ubuntu.com/show_bug.cgi?id=16785](http://bugzilla.ubuntu.com/show_bug.cgi?id=16785)

---

