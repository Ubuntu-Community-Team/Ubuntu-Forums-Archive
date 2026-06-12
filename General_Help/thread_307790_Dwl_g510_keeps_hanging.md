---
title: "Dwl g510 keeps hanging"
date: 2006-11-27
forum: General Help
---

### Post by imjustabill on 2006-11-27
I've got a D-link dwl g510 (rev b) wifi card with an atheros chipset. I can connect to my wireless network just fine, and can usually browse the web normally, but whenever I try do open a large web page or download a large file, my connection basically stops. Generally, download speeds will averages around 200k a second, then suddenly drop off and stop all together. I don't lose my connection, I can still go to another site or start to download another file. I've tried on dozens of different sites and files to make sure it's not just a slow site. My connection seems to be fine, if I simply ping a site I get responses, but when downloading large files it just stops. 

here's the output of iwconfig and ifconfig:
```
root@endor:~# iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"XXXXXX" 
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:E5:06:00   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:C100-EE93-08   Security mode:restricted
          Power Management:off
          Link Quality=42/94  Signal level=-53 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@endor:~# ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:11:95:D4:73:A6  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:506961 (495.0 KiB)  TX bytes:24098 (23.5 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-D4-73-A6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8072 errors:0 dropped:0 overruns:0 frame:3717
          TX packets:1594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1184559 (1.1 MiB)  TX bytes:92720 (90.5 KiB)
          Interrupt:10 Memory:ce0e6000-ce0f6000 



```

Any ideas?

---

