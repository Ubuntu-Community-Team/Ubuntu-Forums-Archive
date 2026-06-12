---
title: "wifi problems"
date: 2015-11-18
forum: General Help
---

### Post by Hodor on 2015-11-18
I have two wifi adapters connected, neither works very well.  I'm running ubuntu 14.04.xx 64 on a custom pc (asrock z97 extreme 6, Intel Core i7-4790K ).

1. I have an Intel Dual Band Wireless AC 7260 Mini PCI-E Adaptor OEM - this is functioning, but I only get very poor connections (I think the antennae I've connected are inadequate);

2. I have a Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter - which the os doesn't seem to be using to connect.  It lists under lsusb (Bus 003 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter), but I'm sure if it was being used to connect me to the router I'd have a better connection that 1 Mb/s (iwconfig)
eth0      no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"...'  
          Mode:Managed  Frequency:2.462 GHz  Access Point: ... 
          Bit Rate=1 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11   Missed beacon:0


eth1      no wireless extensions.


virbr0    no wireless extensions.


lo        no wireless extensions.

When I look under software, additional drivers: nothing shows up.

any advice?
- if there's some tips that will get the intel adapter working better, that would be great.  A better driver?
- otherwise, how do I get the realteck adapter working? Do I need to manually install a driver?
- should I remove the intel adapter?

---

