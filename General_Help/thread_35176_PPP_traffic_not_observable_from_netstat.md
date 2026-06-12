---
title: "PPP traffic not observable from netstat"
date: 2005-05-17
forum: General Help
---

### Post by Consumer on 2005-05-17
Hello,

I have a PPP connection set up and running. I had a script (speedtouchconf) configure my speedtouch 330 ADSL modem and that all works fine. I also have firestarter runing as a firewall on the box. 

When I try and see what connections are being made externally with netstat the only data i can obstain is internal traffic, not the traffic for the PPP connection. I've tried using syntax such as netstat -ta and only ever get data for eth0. 

Is there any way I can get netstat to show me what sockets are connected via ppp to external locations?

thanks,

James

---

### Post by tread on 2005-05-18
I think gkrellm offers a simple interface to displaying the info you want. I dunno too much about netstat though.

---

