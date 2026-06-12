---
title: "[SOLVED] Wireless not working (I Have ndiswrapper or whatever it is called)"
date: 2007-12-26
forum: General Help
---

### Post by patrickaupperle on 2007-12-26
I had my wireless working, then just a few minutes ago it stopped:confused::confused:

i ran sudo iwlist scanning

```
patrick@patrick-laptop:~$ sudo iwlist scanning
[sudo] password for patrick:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:16:B6:CE:BB:53
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:100/100  Signal level:-26 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:18:4D:80:0A:98
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK


```

Can't connect to any networks:confused::confused::confused:

---

### Post by rainwalker on 2007-12-26
I don't know how to fix your problem, but if worst comes to worst and you must get a new wireless card, the Netgear WG511T works perfectly out of the box

---

### Post by thefirstM on 2007-12-26
What type of wireless card do you have?  Could you post an lspci output?

---

### Post by patrickaupperle on 2007-12-27
WOW! I woke up this mourning and it was working again:confused::KS:KS:KS:KS

---

