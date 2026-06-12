---
title: "internet connection in ubuntu 6.1need help"
date: 2007-09-04
forum: General Help
---

### Post by zagloba on 2007-09-04
need help with settinu up internet on ubuntu 6.1 using dsl connection
plz help I do not want to go back to window :)
I did try the help section but no luck.help plz.

---

### Post by prince_niceguy on 2007-09-04
to start off with ...

what is the DSL modem name/model. Does it have ethernet port or is it USB one?

if it has ethernet port then it should not be a big issue as ethernet is very well supported in ubuntu. if it is usb then there would be some work arounds to get it up and running.

---

### Post by zagloba on 2007-09-04
soory Im new in linux ok the modem name is actiontec gt701-wg
and is connectet with ethernet port not usb.

---

### Post by prince_niceguy on 2007-09-04
if it is ethernet port then it should give ip address.

can you type ifconfig in the terminal and post back the results.

---

### Post by mikewhatever on 2007-09-04
You should run pppoeconf command and follow the prompts. For detailed info see the link [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by zagloba on 2007-09-04
i did the pppoeconf and shows that the acces connector did not respond
problem might be another running ppoe process 
i do have win xp on the same comp is this the problem?
some kine of conflict between win and linux?
i do want to get away from windows but need internet 
plz help

---

### Post by mikewhatever on 2007-09-04
No, XP is not the problem. No part of it is loaded while you are running Ubuntu. Try the suggestion of prince_niceguy, and post the output of ifconfig.

---

### Post by zagloba on 2007-09-04
ok how do I post the info from linux system into my xp comp with internet
so u can see.Im new in this be gentle on me plz:):)

---

### Post by krazy1912 on 2007-09-04
bump

---

### Post by mikewhatever on 2007-09-05
> **zagloba said:**
> ok how do I post the info from linux system into my xp comp with internet
so u can see.Im new in this be gentle on me plz:):)

You can save to an external storage, usb stick, floppy, a storage partition readable from both.

---

### Post by prince_niceguy on 2007-09-05
have you tried rebooting the dsl router after login into linux. not sure but that might a issue.

also who is your isp?

---

### Post by zagloba on 2007-09-05
i did the config in terminal and this is what it shows


 eth0       link encap:ethernet hwaddr 00:10:b5:f4:3f:44
       inet addr 192.168.0.2 bcast 192.168.0.255 mask 255.255.0
       inet6 addr fe80::218:b5ff:fef4:3f44/64 scope link
      up broadcast running multicast mtu:1500 metric:1
      rx packets:11 errors:0 dropped:0 overruns:0 frame:0
    tx pockets:17 errors:0dropped:0 overrun:0 carrier:0
    collisions:0 txqueuelen:1000
     rx bytes:1674 tx byts:1620
     interupt:5 base address:0x2000


lo      link encap:local loopback
     inet addr:127.0.0.1 mask:255.0.0.0
     inet6 addr: ::1/128 scop host
     up loopback running mtu:16436 metric:1
      rx packets:2 errors:0 dropped:0overuns:0 frame:0
      tx same as rx
     colission:0 txquequelun:0
     rx byts:100 tx byts:100 
come on some one plz help me with this

---

### Post by zagloba on 2007-09-05
this is what i get in terminal 
eth0 link encap:ethernet hwaddr 00:10:b5:f4:3f:44
inet addr 192.168.0.2 bcast 192.168.0.255 mask 255.255.0
inet6 addr fe80::218:b5ff:fef4:3f44/64 scope link
up broadcast running multicast mtu:1500 metric:1
rx packets:11 errors:0 dropped:0 overruns:0 frame:0
tx pockets:17 errors:0dropped:0 overrun:0 carrier:0
collisions:0 txqueuelen:1000
rx bytes:1674 tx byts:1620
interupt:5 base address:0x2000


lo link encap:local loopback
inet addr:127.0.0.1 mask:255.0.0.0
inet6 addr: ::1/128 scop host
up loopback running mtu:16436 metric:1
rx packets:2 errors:0 dropped:0overuns:0 frame:0
tx same as rx
colission:0 txquequelun:0
rx byts:100 tx byts:100

---

### Post by zagloba on 2007-09-06
come on anyone plz help:(

---

### Post by zagloba on 2007-09-06
somebody plz help

---

### Post by prince_niceguy on 2007-09-07
who is your isp? if you are getting a ip means there is something wrong with the ppoe config. ensure you are putting the correct values in the ppoeconfig.

---

