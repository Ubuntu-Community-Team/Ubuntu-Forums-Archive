---
title: "Network manager and NDISWRAPPER help"
date: 2007-05-28
forum: General Help
---

### Post by rdcmmnst on 2007-05-28
I have installed my wl-138g using ndiswrapper and windows drivers(obviously) this was quite the task for me because i have only been using linux for a couple days. My distribution is feisty fawn.

I can see my network which was initially WPA-Personal protected. I entered the PSK (pre shared key) and could not connect. I then changed the router to broadcast just an open signal no authentication required. I still could not connect. I could see both of the networks and even get a signal strength meter but could not connect. 

I did some research and i think i have two options..either i didn't install the NIC right..or i need a different Network manager. I have read that wicd comes highly recommended and has solved alot of peoples problems. I tried to install wicd but it said that it interfered with Network manager..i then tried to remove network manager through add/remove...it didn't work. 

I am a beginner and would like to know how i can uninstall network manager..safely so that i can get it back on if need be..because i can get connected with a regular wired connection. After uninstalling network manager i can install wicd..unless there is information i need to know.

Any input would be highly appreciated. Thus far i have been extremely impressed with the professionalism of this forum. Well done and thank you in advance

---

### Post by rdcmmnst on 2007-05-28
is there any more information needed?

---

### Post by ivesjd on 2007-05-28
sudo apt-get remove network-manager

---

### Post by rdcmmnst on 2007-05-29
yes, but if i do this and then install wicd and it doesn't work will i be able to connect to the internet, because i might not be able to download the necessary files for network manager.

---

### Post by compwiz18 on 2007-05-29
if you have access to a wired network, then there shouldn't be much trouble with reinstalling network-manager.  I would guess that wicd will work on ndiswrapper, though.

---

### Post by rdcmmnst on 2007-05-29
I installed WICD and could not get connected as WPA 1 client, 

I then went into the router and changed it into an open network. Still no connect. I have since reinstalled network manager and still cannot get connected. Still no connection.. kind of seems frustrating..but probably just because i am a noob any help would be apreciated

Iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:04:E2:AC:4D:ED
                    ESSID:"Cliffhome"
                    Mode:Managed
                    Frequency:2.467 GHz (Channel 12)
                    Quality:7/94  Signal level:-69 dBm  Noise level:-154 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:11:2F:4F:9C:A9  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

iwconfig

wlan0     IEEE 802.11-DS  ESSID:"cliffhome"  Nickname:"unknown"
          Mode:Managed  Bit Rate=54 Mb/s   
          RTS thr=2346 B   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

i don't know if that helps..but thanks again guys

---

### Post by rdcmmnst on 2007-05-29
bump? Any ideas anything will help

---

