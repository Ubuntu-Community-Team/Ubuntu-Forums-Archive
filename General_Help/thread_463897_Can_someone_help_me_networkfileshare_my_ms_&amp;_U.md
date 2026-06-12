---
title: "Can someone help me network/fileshare my ms &amp; Ubuntu cpu's together"
date: 2007-06-04
forum: General Help
---

### Post by swoll1980 on 2007-06-04
My windows settings are
Ip address 192.168.1.10
mask 255.255.255.0
defult gateway 192.168.0.1
dns server 68.94.156.1
alternate dns server 68.94.157.1
work group MSHOME
Can anybody help me set up my unbuntu cpu to work on this network. Is there a away to change fire wall settings. Do I even have a firewall for Ubuntu. Do I need one?

I'm lost
__________________

---

### Post by vanadium on 2007-06-04
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Networking](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Networking)

---

### Post by lazyart on 2007-06-04
Does your modem connect to your PC by a patch cord or USB?  Hopefully it's a patch cord.
Do you have a router?  You'll need one for this...

---

### Post by 13warrior on 2007-06-04
In ubuntu we have a gui tool to assist you in setting up the network. It can be found under System->administration->Network. You can use it to setup your Network. As far as firewalls are considered there are some firewalls available like Lokkit and Gaurddog. 

[http://security.linux.com/article.pl?sid=06/06/26/1556259&tid=13]("http://security.linux.com/article.pl?sid=06/06/26/1556259&tid=13")

---

### Post by freebeer on 2007-06-04
> **swoll1980 said:**
> My windows settings are
Ip address 192.168.1.10
mask 255.255.255.0
defult gateway 192.168.0.1
__________________

Is the above right?  It seems to me that the gateway isn't on the same subnet as the windows machine (.1.x vs .0.x)

---

### Post by jiminycricket on 2007-06-06
Check this out too for file sharing, make sure you do "sudo smbpasswd -A insertusername" too.  [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by swoll1980 on 2007-06-08
both cpus  using same ip address. I try to change one to a static ip it disconects

---

