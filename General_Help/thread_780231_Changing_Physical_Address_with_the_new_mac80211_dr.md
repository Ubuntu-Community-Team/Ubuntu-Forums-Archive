---
title: "Changing Physical Address with the new mac80211 drivers"
date: 2008-05-03
forum: General Help
---

### Post by Friendless on 2008-05-03
The default method i've used would be 

```

ifconfig wlan0 hw ether 00:1c:bf:XX:XX:XX

```

It still changes, however when I actually change the address i'm unable to fully associate with any Access Point, all I get is a, " Not connected ". This is using WicD, had same issue with the default Ubuntu network manager as well. Before changing the physical address it can connect 100% fully with no issues.

While the wlan0 HWaddr will change the wmaster0 remains the same, rather if this is related or now i'm not sure, for I have no idea how the wmaster0 functions within the connection process.

This is not an issue with the Access Point rejecting a connection with the new associated MAC address.

I'm a newbie at linux however I know how to get my way around...

Is there any certain logs I should post along with this?

It's an Intel Pro Wireless 3495 ABG? on an acer laptop.

---

### Post by Zorael on 2008-05-03
Semi-related, but can you scan for any networks or does it consistently end up with no results when you *know* there's a network in range?
```
$ sudo iwlist scan
```


If so, you want to create a file located at **/etc/modprobe.d/iwl3945** with the below contents. Open up a text editor with superuser permissions, such as by hitting Alt+F2 to get a run box and entering '**kdesu "kate /etc/modprobe.d/iwl3945"**'.
```
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1 hwcrypto=1
```

Then restart networking by entering the following in a terminal.
```
$ sudo /etc/init.d/networking restart
```
And see if you can find any networks with the first command.

---

### Post by Friendless on 2008-05-03
Alright, right, I should of mentioned infact I was going to just forgot during the actual post.

I can see any of the local Access Points after changing the Physical Address. The only actual problem exists during the connection process: Can connect before can't connect after.

This has been tested on both self-owned access points and access points hosted by a nearby university which I have full access and full administrator access to as well.

They show up fine, when you stated to create the file in... I assume you wanted me to create the file iwl3945 as the text document itself.

I logged in as root, did a nano /etc/modprobe.d/iwl3945

and entered the information provided.

Restarted the network as provided.

No difference was noted in the situation.

**EDIT (More information):**

Noticed that after the failed connect attempt with the new HWaddr it creates a wlan0:avahi within ifconfig

Noticed avahi has a private IP... i'm guessing this is a common thing which I lacked knowledge about that creates a Private IP.

Looks like some kind of a DHCP issue after changing it... here is some logs from /var/log/daemon.log

> 
May  3 12:50:41 unknown dhclient: Internet Systems Consortium DHCP Client V3.0.6
May  3 12:50:41 unknown dhclient: Copyright 2004-2007 Internet Systems Consortium.
May  3 12:50:41 unknown dhclient: All rights reserved.
May  3 12:50:41 unknown dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
May  3 12:50:41 unknown dhclient:
May  3 12:50:41 unknown dhclient: wmaster0: unknown hardware address type 801
May  3 12:50:42 unknown dhclient: wmaster0: unknown hardware address type 801
May  3 12:50:42 unknown dhclient: Listening on LPF/wlan0/00:0b:6c:6a:42:fd
May  3 12:50:42 unknown dhclient: Sending on   LPF/wlan0/00:0b:6c:6a:42:fd
May  3 12:50:42 unknown dhclient: Sending on   Socket/fallback
May  3 12:50:46 unknown dhclient: DHCPREQUEST of 192.168.2.4 on wlan0 to 255.255.255.255 port 67
May  3 12:50:50 unknown dhclient: DHCPREQUEST of 192.168.2.4 on wlan0 to 255.255.255.255 port 67
May  3 12:50:59 unknown dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  3 12:51:04 unknown dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  3 12:51:12 unknown dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May  3 12:51:29 unknown dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
May  3 12:51:30 unknown dhclient: No DHCPOFFERS received.
May  3 12:51:30 unknown dhclient: Trying recorded lease 192.168.2.4
May  3 12:51:30 unknown avahi-daemon[5180]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.4.
May  3 12:51:30 unknown avahi-daemon[5180]: New relevant interface wlan0.IPv4 for mDNS.
May  3 12:51:30 unknown avahi-daemon[5180]: Registering new address record for 192.168.2.4 on wlan0.IPv4.
May  3 12:51:33 unknown avahi-daemon[5180]: Withdrawing address record for 192.168.2.4 on wlan0.
May  3 12:51:33 unknown avahi-daemon[5180]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.4.
May  3 12:51:33 unknown avahi-daemon[5180]: Interface wlan0.IPv4 no longer relevant for mDNS.
May  3 12:51:33 unknown avahi-autoipd(wlan0)[6858]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
May  3 12:51:33 unknown avahi-autoipd(wlan0)[6858]: Successfully called chroot().
May  3 12:51:33 unknown avahi-autoipd(wlan0)[6858]: Successfully dropped root privileges.
May  3 12:51:33 unknown avahi-autoipd(wlan0)[6858]: Starting with address 169.254.8.27
May  3 12:51:38 unknown avahi-autoipd(wlan0)[6858]: Callout BIND, address 169.254.8.27 on interface wlan0
May  3 12:51:38 unknown avahi-daemon[5180]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.8.27.
May  3 12:51:38 unknown avahi-daemon[5180]: New relevant interface wlan0.IPv4 for mDNS.
May  3 12:51:38 unknown avahi-daemon[5180]: Registering new address record for 169.254.8.27 on wlan0.IPv4.
May  3 12:51:42 unknown avahi-autoipd(wlan0)[6858]: Successfully claimed IP address 169.254.8.27
May  3 12:51:42 unknown dhclient: No working leases in persistent database - sleeping.




Not sure if that's helpful or not...

Going to try and set a static IP with the new MAC and see how it works.

---

### Post by Zorael on 2008-05-03
Maybe there are hardware differences, then. This is how it works for me.

```
zorael@sunspire:/etc/modprobe.d$ cat iwl3945
cat: iwl3945: No such file or directory
*----------- no iwl3945 file*

zorael@sunspire:/etc/modprobe.d$ sudo iwlist wlan0 scan
wlan0     No scan results
*----------- no scan results at all*

zorael@sunspire:/etc/modprobe.d$ sudo mv /home/zorael/iwl3945 .
zorael@sunspire:/etc/modprobe.d$ cat iwl3945
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1 hwcrypto=1
*----------- iwl3945 there now*

zorael@sunspire:/etc/modprobe.d$ sudo modprobe -r iwl3945
zorael@sunspire:/etc/modprobe.d$ sudo modprobe iwl3945
*----------- same as restarting network. I think? Try these commands instead*

zorael@sunspire:/etc/modprobe.d$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:0B:7D:12
                    ESSID:"lappskole"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/100  Signal level=-90 dBm  Noise level=-98 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000004011ac3c51
*----------- works, yay*
```



Try the **modprobe -r iwl3945** and **modprobe iwl3945** combo instead, maybe I messed up by recommending /init.d/networking restart.

---

### Post by Friendless on 2008-05-05
Still no solution has been found...

Is anyone using MAC80211 Drivers able to change their MAC without any issues?

If so what method did you use?

---

