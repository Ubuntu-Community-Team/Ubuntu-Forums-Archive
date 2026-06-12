---
title: "Lost local area network connection after updating Ubuntu 6.10"
date: 2007-04-28
forum: General Help
---

### Post by bluesonix on 2007-04-28
Hello everyone. Hope someone can help me.

I just reformatted my XP/Vista dual boot system, removed Vista and had XP SP2 reinstalled. After reading Ubuntu forums for a week, I finally decided to add Ubuntu 6.10 Edgy Eft. Although I was expecting to run into video card problems, the dual boot installation went smoothly. I was so happy and proud of myself. :) 

As I was in the process of exploring my sweet Ubuntu, I was also downloading the updates. I got a message that I needed 191 updates. I didn't bother to check each and every one of them because I was in the process of setting up the MS Outlook-like program and KVirc [I'm really sorry but I cannot recall the program names]. As prompted, I restarted my pc and when it finished rebooting, the local area connection was gone. I checked the network properties and it is still active. I even had an ip address present [192.168.1.100] 

Is it possible that this was caused by one of the updates? What else do I need to check regarding the network connection properties? I really hope someone can help me because this is really my first dip into Ubuntu. :) 

Thanks everyone! Cheers! :)

---

### Post by zvacet on 2007-04-28
system>administration>network settings>select your modem<properties>select yout type of connection(dhcp or static)>chek upper left box>close>DNS tab>delete address you see there and add your nameservers>close

```
sudo pppoeconf
```

---

### Post by bluesonix on 2007-05-01
> **zvacet said:**
> system>administration>network settings>select your modem<properties>select yout type of connection(dhcp or static)>chek upper left box>close>DNS tab>delete address you see there and add your nameservers>close

```
sudo pppoeconf
```

Thanks for the reply. I am working behind a router so I need not enable the modem. The network icon on my toolbar still detects no connection but when I clicked on Firefox, my homepage loaded. I checked on my other internet programs and they all worked fine. I guess I'll just disregard that network icon as long as internet is still working. :) 



*Bummer... I should have installed Ubuntu ages ago... Ubuntu really rocks!* :guitar:

---

