---
title: "reconnecting internet once disconnected"
date: 2008-06-25
forum: General Help
---

### Post by gurveentaneja on 2008-06-25
Hi!!!! I am new to this forum and new to linux as well. I own an HP pavillion notebook & have installed Xubuntu along with windows vista. But while operating xubuntu, whenever there is a network failure on behalf of the server of my internet service provider or the modem is switched off due to power failure, the internet does not work on restarting the modem, uuntil either i change the configuration from static ip to automatic or any other & then back to static ip or reboot the system.........I am really tired of going through this cycle considering that power failures are pretty common in my area in this part of the year..........U people will not believe but i had to do the same twice while making this post........please help.....

---

### Post by caljohnsmith on 2008-06-25
I'm not sure I'm clear on your exact configuration--are you using ethernet (DSL/cable connection) or are you using a phone modem (PPP connection)? Or is it something else?

Whichever you are using, if it is configured in the /etc/network/interfaces file, you can use "ifup" and "ifdown" to bring up or down your internet connection. For instance "sudo ifup eth0" would bring up a ethernet connection, but give it your correct interface. You can use "ifconfig" to find your interface. 

If that doesn't work then please give the information from "ifconfig" and we can go from there.

---

### Post by ybd on 2008-06-25
I'm by no means an expert but I've had similar power outs in the last few days and what worked for me was right clicking the Network symbol on the task bar (near the clock) and unchecking Enable Networking, and reenabling it.

---

### Post by gurveentaneja on 2008-06-25
> **caljohnsmith said:**
> I'm not sure I'm clear on your exact configuration--are you using ethernet (DSL/cable connection) or are you using a phone modem (PPP connection)? Or is it something else?

Whichever you are using, if it is configured in the /etc/network/interfaces file, you can use "ifup" and "ifdown" to bring up or down your internet connection. For instance "sudo ifup eth0" would bring up a ethernet connection, but give it your correct interface. You can use "ifconfig" to find your interface. 

If that doesn't work then please give the information from "ifconfig" and we can go from there.

Thanks a lot caljohnsmith...........your advice worked........all the three commands that is, 'ifup','ifdown' & 'ifconfig' worked and seem quite handy......

---

