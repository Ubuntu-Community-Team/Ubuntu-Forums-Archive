---
title: "Wlan will not work..."
date: 2005-10-26
forum: General Help
---

### Post by Argon on 2005-10-26
Hi!

I am an Ubuntu newbie..  My Wlan-card appears in System-Network "network configuration". It says that the card is active. However, when i choose wlan0 to be my default gateway-unit it will not connect to my wlan. If I restart, it just hangs for a long time searching for my network. Then it fails to connect and starts ubuntu without a network. What am I doing wrong?

Argon

---

### Post by soul_rebel on 2005-10-26
You are a gnu-linux newbie, not only a ubuntu newbie I think. I think you should start learning hard or get yourself a more newbie friendly distro, like SuSE.

If you want to stick with ubuntu, then post a lot of infos about your hardware and wireless network, one can't help without infos. bye

---

### Post by malacandra on 2005-10-26
Another helpful reply to a simple request for help....:rolleyes: 

Argon,

try the following.

My wireless card is wlan0. So substitute whatever you have.

Try the following to get things back to scratch:

Open a terminal, change to root (or sudo)

[B]killall dhclient
ifconfig eth0 down
ifconfig wlan0 down[/B]

That will shut everything down.

Then try:
**ifconfig wlan0 up** to turn the wlan back on.

**iwlist wlan0 scan**

That should show you any wirless networks the card can see.

Assuming you have a network in view do this:

**iwconfig wlan0 essid networkname key 123EFDetc**

After that, type

**iwconfig**

Check to see that your wireless card is actually connected to the network.

Then try:

**dhclient wlan0**

That should get you and IP and you're all set.

You might also keep in mind the following:
[B]
iwconfig wlan0 txpower on [or off][/B]

That will turn the wireless radio on or off. My laptop has a kernel that has it hardwired to the function key but that's how you do it from the CL.


Finally, to get this as your default connection, edit [b]/etc/network/interfaces

(use a text editor like gedit; you've got to do it as root or sudo)

Comment the line **auto eth0**

And uncomment the **auto wlan0**

You can then add a line for essid="network name" and key="123EDFetc" 

Let us know how that works.

---

### Post by Argon on 2005-10-27
Thank you for a good reply! :)

I did what you said, and I could not get it to work. 
Here is the result:

argon@ubuntu:~$ sudo killall dhclient
Password:
dhclient: drepte ingen prosess
argon@ubuntu:~$ sudo ifconfig eth0 down
argon@ubuntu:~$ sudo ifconfig wlan0 down
argon@ubuntu:~$ sudo ifconfig wlan0 up
argon@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:3C:71:64
                    ESSID:"linksys_SES_37759"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-74 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

argon@ubuntu:~$ sudo iwconfig wlan0 essid linksys_SES_37759 key 1850347277
argon@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"linksys_SES_37759"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:3C:71:64
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Encryption key:1850-3472-77   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:-58 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

argon@ubuntu:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0d:f0:10:46:0e
Sending on   LPF/wlan0/00:0d:f0:10:46:0e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
argon@ubuntu:~$


Am I doing something wrong?

-Argon-

---

### Post by soul_rebel on 2005-10-27
EDIT: wrong suggestion, removed. Sorry.

---

### Post by malacandra on 2005-10-28
Argon,

Everything looks fine. Are you sure the router is set up correctly?

Seems like it doesn't  want to assign and IP address.

Is it DSL? Cable? Something else? Have you used this wireless network before?

---

### Post by teddy69 on 2005-10-28
I sometimes get that same message:
```
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

what I usually do is just reset the router (turn it off then back on, not reset it completly), wait a few minutes then ifdown wlan0 and then ifupwlan0 and if it's now working correctly you shouldn't get any of those messages up there...sometimes switching channels works too, but you might be having different troubles than mine, still worth the try though

---

### Post by edwardog on 2005-10-29
Hey Argon (what a noble name...),

What kind of security are you using on your router?  The method so far described in this post
```
$ sudo iwconfig wlan0 essid linksys_SES_37759 key 1850347277
```
will only work if you're using WEP -- for WPA and WPA2 you have to install wpa_supplicant and fiddle with the config files.  Let me know if you want to do that instead.

I also noticed that the results from iwlist scan suggest that encryption isn't turned on by the router ("Encryption key = off").  Could you please confirm that encryption is active router-side?

You might also want to search the forum for posts that mention your wireless card just in case it needs something like ndiswrapper (a Linux tool used to let your kernel be able to use original Windows drivers).  I find that using an advanced search and showing your results as posts finds relevant things faster.

Good luck!

---

### Post by Argon on 2005-10-30
Hey all!

I have been fiddling with my router today. I have turned off all wireless security just to make it easier to make it work. I also have installed GTKWifi which seems to get a 100% connection to my router (but it says that dhcp fails when connecting). My router is new, and I am currently online throught it using cable. I have never gotten the wireless connection to work. However... I am reading the user manual for my router again, and it seems like the problem might have something to do with the fact that the router is using SecureEasySetup (which I have never heard of..). I am currently digging into this matter...

Argon

---

### Post by malacandra on 2005-10-31
Argon,

If you are using cable/or DSL modem then you CANNOT have the router doing the DHCP. Usually the best way to do it is to configure the actual modem as for "pass-through" and let the router assign DHCP. Don't use easy setup, go in and do it your self.

Should be these steps:

(1) Configure modem to run as "pass through" (using modem config webpage)

(2) Setup Router as DHCP server. Usually the router is on webpage 192.168.1.1 or close to that.

That should be it. Try it unsecured and if that works then try it with a WEP key or other type.

Let us know!

---

### Post by edwardog on 2005-10-31
[QUOTE=malacandra]Argon,

If you are using cable/or DSL modem then you CANNOT have the router doing the DHCP. Usually the best way to do it is to configure the actual modem as for "pass-through" and let the router assign DHCP. Don't use easy setup, go in and do it your self.

Should be these steps:

(1) Configure modem to run as "pass through" (using modem config webpage)

(2) Setup Router as DHCP server. Usually the router is on webpage 192.168.1.1 or close to that.

That should be it. Try it unsecured and if that works then try it with a WEP key or other type.

Let us know![/QUOTE]

I think this needs some clarification (malacandra, please correct any assumptions I'm making here):

Certain "modems" being sold or rented out today are actually modem/router/multi-port switch combinations.

The role of the modem part is basically to turn the "sounds" heard on the phone or cable line into ethernet packets.

The role of the router part is to connect the WAN (the ISP side) to your LAN (the side inside your house).  Wikipedia has a great article on this: [http://en.wikipedia.org/wiki/Router](http://en.wikipedia.org/wiki/Router)

The role of the switch part is to let the different devices with IPs connected to the "switch part of the box" talk to each other, and to an uplinked IP range if need be (the WAN, or ISP side in this case).

Additionally, some routers come with things like DHCP servers that dole out and keep track of IP addresses in a network.

In my case, I have an actual adsl modem (no router part or switch part) connected to the WAN (aka uplink in this case) port of a router (router + switch, but no modem), which runs a DHCP server.

In some other cases (like those pertaining to these new "modems"), it's actually a modem+router+DHCP server.  Crazy, eh?

I think what malacandra is getting at is that some setups involving one of these new combo "modems" connected to a "router" result in there being 2 DHCP servers.

While this should technically work (the "modem"'s plug would go into the "router"'s WAN port, resulting in the "modem" being in its own network, and the "router"'s switch having another), it sometimes leads to a total muckup of things as there are 2 DHCP servers sometimes trying to give IPs out when they shouldn't.

To configure the "modem", plug straight into it (bypass the "router"), and follow the manufacturer's instructions.

As a final note, I'd also like to point out that if you have the ability to use WPA instead of WEP, do it, as WEP can be broken within a *short* period of time (see google for an idea of how long *short* is).

Good luck with the fight!

---

### Post by Argon on 2005-10-31
Hi again!

I have been able to get a windows pc up and running using the wan.
But still, Breezy will not work... 
DHCP seems to work fine using cable, as I am online using it, but when it comes to the wlan, I have DHCP failure... Shouldn't the dhcp either work or not work? In other words: If it works on cable, shouldn't it work on the wlan?
It is early in the morning, I have been working all night and should be getting some sleep. Maybe this is not a good time to be doing this.... the graveyard shift is hard sometimes...

By the way, I tried to find "pass through" or bypass on the modems config webpage, but could not find it. However I was able to "not use" dhcp on the modem, but nothing changed. Well, sleep now, work later... See ya!

Argon

---

### Post by lupine_nickt on 2005-11-01
The other thing you could try - assuming that your modem is actually a modem/router - is to simply not use DHCP for your wlan0 interface... assign your own (this is what I'm doing on mine). So, for example, if your router has an IP address of 10.0.0.2, you'd assign your PC a similar IP - say, 10.0.0.128. You'd also need a subnet mask (which for any IP in the range 10.0.0.0-10.255.255.255 would be 255.0.0.0), and your gateway would be your router's IP address (ie. 10.0.0.2)

The other common configuration is for your router to have 192.168.0.1 (or .1.1, but they're more or less the same)... in that case, you'd just substitute the network mask to 255.255.255.0, and your available local IP addresses becomes 192.168.0.0 to 192.168.0.255. 

As for actually *doing* this, it's a bit of a pain on the command line, so you're best off in System->Administration->Networking. Select your wlan0 interface, goto configure, and un-check the 'configure automatically' box... fill in the IP address, subnet mask, etc, etc. 

Your modem/router should act as a DNS server as well... you might need to turn it on (usually it's called DNS Proxy); in which case, you can simply put it's IP address in the DNS section. Otherwise, your ISP can tell you which IP addresses their DNS servers are on, so you can do it from there.

NOTE: If you have an ethernet cable box, and you've plugged a wireless "access point" into it, then the cable box might have it's own IP address... in which case, you need to use IT'S IP address as the gateway, and your ISP's DNS servers.


HtH

xF,

...Nick

---

