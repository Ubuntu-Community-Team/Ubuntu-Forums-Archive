---
title: "intel 4965 problem in Ubuntu Studio Hardy"
date: 2008-05-17
forum: General Help
---

### Post by kensuguro on 2008-05-17
I thought Studio and normal distribution is the same.. 4965 problem seems to have been resolved in normal Hardy, as ubuntu claims it works out of the box in the hardware compatibility list:
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700)

So I installed Ubuntu Studio, and 4965 is definitely acting strange.  During installation, wifi wasn't detected so I skipped network config during install.  After I got to desktop, wifi comes up in lspci and iwconfig just fine
wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I am trying to connect to a open network, with mac address filtering (works fine in vista), so I go to network tool in administration... and am not sure which password type to choose because there is none.  I type in my ESSID..  and iwlist wlan0 scan shows nothing.

So I go back, turn on wpa security on my router, and go back to network tool in administrator.  I change password type to wpa pesonal, and type in password.  This time, iwlist wlan0 scan shows a whole list of stuff, including my Funk-Air network.

Seems all has gone well, but iwconfig still shows the same thing.


One strange thing tho..  when I do ifconfig, I see 2 devices that don't exist:
eth0      Link encap:Ethernet  HWaddr 00:1c:7e:bc:5b:a6  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:7eff:febc:5ba6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1869 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1163545 (1.1 MB)  TX bytes:311851 (304.5 KB)
          Base address:0xcf80 Memory:ff9c0000-ff9e0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76600 (74.8 KB)  TX bytes:76600 (74.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:46:c5:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1f:3b:46:c5:95  
          inet addr:169.254.7.101  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3B-46-C5-95-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi, and wmaster0..  I'm not really sure where those came form.  But what's strange is wlan0:avahi shows the same mac address as wlan0, which is the one that exists.

Perhaps I should just install normal Hardy, and install Ubuntu Studio Desktop over that?  Or does that not work like it did in Gutsy?

---

