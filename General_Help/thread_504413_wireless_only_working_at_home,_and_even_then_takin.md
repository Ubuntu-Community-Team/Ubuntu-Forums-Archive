---
title: "wireless only working at home, and even then taking forever..."
date: 2007-07-19
forum: General Help
---

### Post by bishop9226 on 2007-07-19
ubuntu feisty x86 on e1505 dell core duo

installed it as well as my wireless setup.  it was working great for awhile, everything would connect.  i even did the tweak to turn off having to enter the keyring over and over and everything still worked.

now all the sudden its been taking FOREVER to connect at home and when it does it works fine.  but when i go anywhere else, school, hotels, places with free wifi, it wont work at all.  it sees the signals and it sits there and attempts to connect but to no avail.  i first noticed it at the bookstore when it took an extra long time to let me on their wireless network.  i thought it was just them but when i booted back to xp i connected in an instant, same everywhere else too.  but now i cant seem to get on anyone's wireless network and its REALLY annoying because then i have to go to XP to use wifi if im not at home.  anyone experience this problem or have any ideas?

thanks

oh and...i did this on my laptop while i was connected.  doubt its much use that waybut ill have to wait til im having trouble elsewhere than home.  its funny because i just rebooted and eventually it worked. kind of annoying how flakey it is.

> art@art-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"gleek"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:E9:77:F8:DC   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

art@art-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:15:E9:77:F8:DC
                    ESSID:"gleek"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  

art@art-laptop:~$ 


---

### Post by anubhavrocks on 2007-07-19
Although this is not a solution,Have you tried wifi-radar?
sudo apt-get install wifi-radar

---

