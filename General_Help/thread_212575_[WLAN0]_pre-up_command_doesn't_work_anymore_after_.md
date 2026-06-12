---
title: "[WLAN0] pre-up command doesn't work anymore after the upgrade to 6.06 LTS..."
date: 2006-07-10
forum: General Help
---

### Post by raoul_is_a_nerd on 2006-07-10
Hi,

My wireless connection was working perfectly well before the upgrade to the Dapper Draker version.

The iwconfig commands (to define the "channel" and the "mode" parameters of my wireless connection)  were executed seamlessly through the /etc/network/interfaces file pre-up command.

The wlan0 came up automatically at startup without any manual intervention.

Life was good.

I still use ndiswrapper. Shouldn't raise any issue : the module is loaded properly.

Now - I mean : since I have upgraded my machine - I need to launch the /etc/network/pre-up-wlan0 script manually, and then the wireless connection starts to work again.

**It has the same behavior as if the pre-up command line from the /etc/network/interfaces file would have been commented :confused: **

Here is my /etc/network/interfaces configuration file :

> 
iface wlan0 inet static

pre-up /etc/network/pre-up-wlan0

	address 192.168.0.6
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
	dns-nameservers 192.168.0.1
	wireless-essid WORKGROUP
	wireless-key s:somethingsecret^^'

auto wlan0



Here is my /etc/network/pre-up-wlan0 script :

> 
#/bin/bash

sudo iwconfig wlan0 mode ad-hoc
sudo iwconfig wlan0 channel 11

exit 0


Has anyone met the same kind of problem ?


Please note :
> 
pre-up iwconfig wlan0 mode ad-hoc
pre-up iwconfig wlan0 channel 11

Already tested : does nothing more than the procedure detailed above...


Regards.

---

### Post by raoul_is_a_nerd on 2006-07-13
Up

---

### Post by panurge77 on 2006-07-13
My card needs to get a key before the essid, so I had to put the key setting line before the essid one on the script

---

