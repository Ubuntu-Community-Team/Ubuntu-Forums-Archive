---
title: "Netgear WG111v3 not working"
date: 2014-04-12
forum: General Help
---

### Post by kwasek2 on 2014-04-12
Hello
I have lubuntu 13.10 x86 with AMD Duron 1.6/Nvidia 5900fx/1gb ddr(on Motherboard but system shows me 768mb.) and WG111v3 wi-fi dongle.
I wanted to get internet by this dongle but in internet settings i have only ethernet and my android phone modem

Iwlist scan
```
wiola@wiola-Uknown:~$ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 80:A1:D7:2B:34:93
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"342"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b040cef4b0
                    Extra: Last beacon: 9040ms ago
                    IE: Unknown: 0003333432
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601050600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020004127A
                    IE: Unknown: DD07000C4300000000

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

usb0      Interface doesn't support scanning.


```
can you help me install this modem?

---

### Post by gordintoronto on 2014-04-12
Please show us the result of lsusb

Or you could have a look at:
[http://ubuntuforums.org/showthread.php?t=1822758](http://ubuntuforums.org/showthread.php?t=1822758)

(I found it by googling WG111v3 linux)

---

