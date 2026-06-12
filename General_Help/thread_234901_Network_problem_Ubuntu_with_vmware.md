---
title: "Network problem Ubuntu with vmware"
date: 2006-08-12
forum: General Help
---

### Post by gekkos on 2006-08-12
Hi,
I am running vmware on XP with Ubuntu 6.06. I want to configure my network using Bridged Network Connection but I get no IP address from my DHCP server. DHCP is working as I become IP address for my XP box. How do I have to configure vmware to work with Ubuntu.
Thanks

---

### Post by ifokkema on 2006-08-12
You've got VMware installed on XP, and Ubuntu running through VMWare?

VMWare should take care of the network connection between your Windows and Ubuntu instances. You don't need an own DHCP...

---

### Post by rbmorse on 2006-08-12
What happens if you tell VMware to use DCHP?

---

### Post by djsroknrol on 2006-08-12
I've never used VMware inside of MS but maybe you might try NAT instead of Bridged?

---

### Post by gekkos on 2006-08-12
This is my vmware config, where can I enable DHCP for Bridged Network Connection. I think I overlook something. See attach

---

### Post by ifokkema on 2006-08-12
Hmm... I think what djsroknrol said makes a lot of sense; just use NAT and you should be up and running...

---

### Post by slakkie on 2006-08-12
From what I understand from vmware and the networking part and a bridged network.

Within Ubuntu (which is loaded in vmware), you can do two things, 1) staticly define your IP address or 2) make sure you configure your network with dhcp.

Try using 'dhclient eth0', and run tcpdump ('sudo tcpdump') to see what happens with the DHCP requests. This might help you locate the problem.

---

### Post by djsroknrol on 2006-08-12
gekkos;

try the second radio button and go from there...seems like to me you have to configure it a little to suit your needs...

---

