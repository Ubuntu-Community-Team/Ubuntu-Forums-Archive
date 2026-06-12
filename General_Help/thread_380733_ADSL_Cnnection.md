---
title: "ADSL Cnnection"
date: 2007-03-10
forum: General Help
---

### Post by jobymathew on 2007-03-10
I have recently installed Linux Ubuntu in my system.  I am using ADSL Connection.  Now the problem is as soon as I have got connected to the Net, I am getting disconnected.  I had set up the connection through sudo pppoeconf.  When I logon through pon dsl-provider, I am getting disconnected immediately.

Please help

---

### Post by zvacet on 2007-03-10
system>administration>network setting>highlight your modem>properties
in new window select your type of connection and chek box in upper left than close
click on DNS and delete address you find there and put your own.close.
```
sudo pppoeconf
```
If this doesen´t work try rp-pppoe.I don´t know what Ubuntu do you use,so I will give guide for Dapper and Edgy.
For Dapper
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")
Edgy
[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")

but in this case you have to replace Exec=gksudo /opt/rp-pppoe-3.8/go-gui with
Exec=gksudo tkpppoe
Restart.You wil find rp-pppoe in programs>internet.In case you don´t get GUI
```
sudo -i
```
```
cd /opt/rp-pppoe-3.8
```
```
./go
```

---

