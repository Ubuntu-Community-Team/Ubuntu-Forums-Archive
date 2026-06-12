---
title: "Connect 3 VM (Ubuntu) with hiding Middle VM"
date: 2016-11-16
forum: General Help
---

### Post by arjunjoshi89 on 2016-11-16
HI,

I have 3 VM (Ubuntu) connected. Vm1(eth0)---->(eth0)VM2(eth1)------>(eth0)VM3. There is internal NAT network between VM1 and VM2. Same for VM2 and VM3. I did iptable forwarding in VM2. I have also set route in VM1 and Vm3. I am able to ping VM3 from VM1. 

While I am pinging VM3 from VM1, I am also checking tcpdump and wireshark on VM3. I am getting IP address of VM2 (eth1) during this analysis. I want to hide IP address of VM2. 

Which changes do I need to on VM2 so while checking on VM3, I will get IP address of VM1 only?

[IMG]https://forums.virtualbox.org/images/smilies/icon_rolleyes.gif[/IMG]

---

### Post by wildmanne39 on 2016-11-16
Welcome to the forum!

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.
Thanks

---

### Post by yulunsus on 2017-02-28
> **arjunjoshi89 said:**
> HI,

I have 3 VM (Ubuntu) connected. Vm1(eth0)---->(eth0)VM2(eth1)------>(eth0)VM3. There is internal NAT network between VM1 and VM2. Same for VM2 and VM3. I did iptable forwarding in VM2. I have also set route in VM1 and Vm3. I am able to ping VM3 from VM1. 

While I am pinging VM3 from VM1, I am also checking tcpdump and wireshark on VM3. I am getting IP address of VM2 (eth1) during this analysis. I want to hide IP address of VM2. 

Which changes do I need to on VM2 so while checking on VM3, I will get IP address of VM1 only?

[IMG]https://forums.virtualbox.org/images/smilies/icon_rolleyes.gif[/IMG]


Hi,

Could you explain how you specify the connections VM1 eth0 to VM2 eth1, and VM2 eth1 to VM3 eth0.
Did you use LAN segment to connect specific interface to another?  and which settings did you do with iptable forwarding, and route setting in VM1 and VM3 ?

Ethan

---

