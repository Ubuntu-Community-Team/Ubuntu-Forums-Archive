---
title: "Internet connection"
date: 2007-03-14
forum: General Help
---

### Post by heresau on 2007-03-14
Hello,

I have become a new Ubuntu user last nite when I finally gave up on Windows and Microsoft. Please tell me how difficult is Ubuntu to run for someone with limited knowledge about computers, operating systems etc. Almost everybody at my workplace recons that it is difficult because it is Linux based program?!
How can I configure internet access, voip etc
Please help,

Stan

---

### Post by zvacet on 2007-03-14
system>administration>network setting>highlight your modem>properties
In new window select type of connection you want(dhcp,static),chek upper left box>close
Click on DNS and delete address you see and put your own>close
```
sudo pppoeconf
```
If this solution doesn´t work try rp-pppoe
if you use Dapper
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")
if it is Edgy 
[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")
but replace Exec=gksudo /opt/rp-pppoe-3.8/go-gui with Exec=gksudo tkpppoe
programs>internet>rp-pppoe
if you don´t get GUI then
```
cd /opt/pr-pppoe-3.8
```
```
sudo ./go
```

---

