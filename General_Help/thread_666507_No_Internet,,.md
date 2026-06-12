---
title: "No Internet,,"
date: 2008-01-13
forum: General Help
---

### Post by xnoor on 2008-01-13
hello,

im facing a strange problem here, i have a linksys wireless router setup and works, my encryption is WPA\TKIP and on ubuntu my wireless card connects to it with no pronblems, but there is not internet and i can't ping, i thought that  this is a problem i get connected to some hot spots but not on my Access Point, here is the output of ifconfig and iwconfig since i dunno where to start

noor@Noureddine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Noor"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:3F:FC:1C   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=94/100  Signal level=-32 dBm  Noise level=-33 dBm
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0

noor@Noureddine:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:7F:92:90  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:DF:1F:E1  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fedf:1fe1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:4 dropped:13 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24596 (24.0 KB)  TX bytes:22347 (21.8 KB)
          Interrupt:17 Base address:0xe000 Memory:f9fff000-f9ffffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:591 errors:0 dropped:0 overruns:0 frame:0
          TX packets:591 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55041 (53.7 KB)  TX bytes:55041 (53.7 KB)

any help or suggestion are is appreciated

Regards,

Noor

---

### Post by xnoor on 2008-01-14
can any one help please, my networkcard is intel PRO/WIRELESS 3945ABG

thank you

---

### Post by articpenguin on 2008-01-14
try 
[http://ubuntuforums.org/showthread.php?t=169593]("http://ubuntuforums.org/showthread.php?t=169593")

[http://ubuntuforums.org/showthread.php?t=647971&highlight=intel+PRO%2FWIRELESS+3945ABG]("http://ubuntuforums.org/showthread.php?t=647971&highlight=intel+PRO%2FWIRELESS+3945ABG")

---

