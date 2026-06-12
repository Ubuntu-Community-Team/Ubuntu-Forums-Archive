---
title: "WiFI randomly dying"
date: 2017-12-08
forum: General Help
---

### Post by maxboivin2 on 2017-12-08
Hello,

I have this problem that is driving me crazy and I can't seem to find any solution online.  I haven't posted here in a while since I usually can solve all my issue by googling but, this one, no dice.

My Wifi keeps dying randomly (a few times a day).  At first, I thought it was after a period of inactivity but, no, it also happens when I'm using it.  And when I say "dying", I don't mean it doesn't just disconnect, it disconnects and can't see any connections.

The problems appeared a few weeks ago, I'm not sure what changed.

Maybe I should start with some details...

My iwconfig output[INDENT]
wlp38s0   IEEE 802.11  ESSID:"linksys"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 14:91:82:E0:AF:42   
          Bit Rate=6.5 Mb/s   Tx-Power=20 dBm   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:16  Invalid misc:138   Missed beacon:0


lo        no wireless extensions.


enp37s0   no wireless extensions.


[/INDENT]
As you can see, power management is already off.

nmcli g output before the problem[INDENT]
STATE      CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN    
connected  full          enabled  enabled  enabled  enabled 


[/INDENT]
nmcli g output after the problem (I'm going out of memory here...)[INDENT]
STATE      CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN    
disconnected  none          enabled  enabled  enabled  enabled 

[/INDENT]

nmcli version: 1.8.4

It might be worth noting that I'm using Wicd... I'm not too sure why anymore, I think it was to fix some speed issues.

The content of my NetworkManager.cong
[INDENT]main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false


[device]
wifi.scan-rand-mac-address=no


[/INDENT]
As you can see, the random mac address is already disabled.


I'm not too sure if there is other information that could be relevant.


When the problem appears, the only way I found to resolve it is to reboot the machine; quite annoying when you're trying to be productive.  Restarting NetworkManager and/or Wicd doesn't fix the issue.  

I saw someplace people talking about doing "nmcli nm" with some other options (status?  sleep?) but nmcli doesn't let me do anything with nm; it says the option is invalid. 

So, here I am, out of idea...


Thank you for your time.

---

