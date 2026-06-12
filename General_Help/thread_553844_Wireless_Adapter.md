---
title: "Wireless Adapter"
date: 2007-09-18
forum: General Help
---

### Post by Doyley on 2007-09-18
Hi all,

I used to use SuSE years ago but I'm a bit unexperienced with Linux now so please bear with me.

I have installed Ubuntu fine and everything is working great apart from my wireless adapter.  I have a Linksys WUSB54GR.  From what I can tell, Ubuntu has reconginzed the device but it is not letting me connect to my wireless network.

It gives me the dialog asking for my password etc which I have entered but it is still not letting me connect.

Can anybody offer any advice?

Thanks!!

---

### Post by mvs1207 on 2007-09-18
This has been answered before as well.  Here is the gist.  

The problem is due to NetworkManager which fails to connect to your wireless router.  I would do this in a terminal

> 
sudo iwlist scan


The above command would show all the wireless network in your neighborhood along with the paramaters.  It would be useful to note down your routers paramaters. From now on I am assuming your wireless interface is named wlan0.  If it is something other than wlan0, substitute that wherever wlan0 occurs.  I am also assuming that your wireless router also acts as DHCP server

> 
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid <YOUR WIRELESS ROUTER's ESSID>
sudo iwconfig wlan0 key   <YOUR KEY>
sudo dhclient wlan0


You should be able to use your wireless network interface.  If the above succeeds then you could put these lines in /etc/network/interfaces in wlan0 section for getting your wireless card working automatically on reboots.  The section would look something lilke this:

> 
auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid <YOUR WIRELESS ROUTER's ESSID>
pre-up iwconfig wlan0 key   <YOUR KEY>


---

### Post by Doyley on 2007-09-18
Many thanks for your reply.

I tried out your suggestion.  When I run sudo iwlist scan in a terminal I get the following..

> 

lo  Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning : Operation not supported.
wlan0  No scan results



There are wireless networks in range.  I boot back into Vista and I connect to my network and I also see my neighbours network.

---

### Post by mudashuda on 2007-09-18
Hi all!

I've been experincing almost the same problem. My o/s is ubuntu 6.06, i installed ndiswrapper & disabled bcm43xx module.

Nothing changes when i run this commands what  is likely to be the problem. 

Not associating with the access point and not taking the essid, but takes the wep key.

victor@testing-pc:~$ sudo iwconfig eth1 ESSID KCWirelessRosa
victor@testing-pc:~$ sudo iwconfig eth1 ap 00:19:56:E0:13:E0


victor@testing-pc:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:0123-4567-89   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



victor@testing-pc:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:19:56:E0:13:E0
                    ESSID:"KCWirelessRosa"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-83 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:19:56:E0:05:40
                    ESSID:"KCWirelessMarx"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-90 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:19:56:E0:14:70
                    ESSID:"KCWirelessboardroom"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-86 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:19:CB:3C:DA:01
                    ESSID:"ZyXEL"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-94 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202

---

### Post by Doyley on 2007-09-19
OK I have it sorted, kind of.

I noticed when running the scan command that sometimes my network would show up which led me to think it was a weak signal.  I don't understand this because if I reboot into Vista I get Good/Very Good signal strengh.
So out of curiosity I dug out my old PCI adapter and tried that.  Once I installed the drivers with ndsiwrapper it worked perfectly.
It's strange, my newer adapter is supposed to be better.  Does Ubuntu have a problem with USB adapters?

---

