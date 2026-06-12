---
title: "VIrtualBox - Networking Problems"
date: 2007-03-29
forum: General Help
---

### Post by MK_MIke on 2007-03-29
Hello,

First off, i'd like to say though is my first post on this forum lots of times to bug fixes and informaion on ubuntu and i think you all great, also i'm still a newbe (1 and a half years old linux user) so could you post your replays in plain english for me :)

My Problem is that i want to run a Virtual Machine using VirtualBox but i need to have it connected to my network on the same ip range and the rest of all the computer also the VM needs to have a static ip address (10.10.0.6). I've tried setting up bridging but i couldn't get it to work and if i use NAT instead of bridging my VM can't be set to a static ip address and it get assigned to a ip address thats not in my network range :S


note: Also my VM networks is being limited to 10mbps!!! any ideas?

-- IP Info i want for the VM
IP Address: 10.10.0.6
Sub Net Mask: 255.255.0
Gateway: 10.10.0.1
DNS: 10.10.0.1

Thanks,

Michael Knights

---

### Post by bodhi.zazen on 2007-05-22
This is for an ubuntu host :

[http://doc.gwos.org/index.php/VirtualBox#Networking](http://doc.gwos.org/index.php/VirtualBox#Networking)

---

