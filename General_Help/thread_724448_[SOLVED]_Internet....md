---
title: "[SOLVED] Internet...?"
date: 2008-03-14
forum: General Help
---

### Post by elbone on 2008-03-14
Okay I absolutely love Ubuntu but the Internet won't work

this also happens with my Vista (same computer) I always will have to click "Diagnose and Repair" but with Ubuntu I see no Diagnose or Repair thing whatsoever 

please help :'(

---

### Post by djamu on 2008-03-14
It's highly  unlikely one of your OS's ( vista +ubuntu ) is responsible 
you propably have a broadband cable / adsl  router/modem combo...

-1. if your computer(s) are using dhcp ( if you didn't fill in IP nrs manually ) 
it's either a dns or gateway related problem ( your modem/router provides the wrong dns / gateway )
Your router / modem has an administrative webpage, if your gateway address ( the address of the router ) is 192.168.0.1 > goto either [http://192.168.0.1](http://192.168.0.1) or [https://192.168.0.1](https://192.168.0.1) some routers use a different port then the standard port ( 80/443 ) check your manual for that... 

-2. if you fill in IP's manually, check that you also filled in a gateway IP address ( usually the same as the router address & different from the one your computer has. usie also the same for the DNS address ( normally your router/modem acts as a dns relay ).


cheers

---

### Post by elbone on 2008-03-14
my router adress thing is 192.168.1.1 and i do not know how to change the ports :s

---

### Post by djamu on 2008-03-14
K

Listen I can't help you if you don't answer my questions ....

---

### Post by elbone on 2008-03-14
Okay I let the DCHP go in automatic, and i connect to the Network but the internet does not work.

In the Vista Machine I have to click Diagnose and Repair I just need an equivalent for Ubuntu.

---

### Post by djamu on 2008-03-14
> **elbone said:**
> Okay I let the DCHP go in automatic, and i connect to the Network but the internet does not work.

In the Vista Machine I have to click Diagnose and Repair I just need an equivalent for Ubuntu.

If you're using DHCP then it's clear that your router is configured wrong. Having an equivalent of that vista stuff doesn't really solve a network misconfiguration ( if I knew of an equivalent )..
after "fixing" the network in Vista start the commandline interface and issue following command > ipconfig, note down all nr.

The easiest route is then to configure your ubuntu network manually ... 
Just pick any IP that matches the netmask or use all the info from the "ipconfig"


 ( so normally your netmask = 255.255.255.0 ) if router IP = 192.168.1.1 chose > 192.168.1.xxx   ( xxx = 1 to 255 but don't use 0 / 1 / 255 )

gateway = router IP¨> 192.168.1.1
dns = router IP > 192.168.1.1  ( assuming dns relay isn't messed up )

all assuming the router = 192.168.1.1

or just reset that router to factory settings as it is clear to me that someone "played"  with the settings ( after noting down your ISP login info )


K.

---

### Post by Patrick-Ruff on 2008-03-14
lol don't ever try looking for something equivilant to 'diagnose and repair' in ubuntu ;).  you'll need to learn a little bit but you'll be able to fix problems yourself without using some tool (that doesn't exist on ubuntu.)

---

### Post by elbone on 2008-03-15
Thank you so much I reset the router and reconnected the ethernet cord and it works :D

thank you :)

---

