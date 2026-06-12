---
title: "Internet slow in Breezy!!!"
date: 2005-10-25
forum: General Help
---

### Post by vempire on 2005-10-25
Hi i from mexico  my problem:

i have a laptop compaq presario m2000 with 512 ram ,amd sempron 2800+ (1.6 ghz) 
i have a network card
Broadcom 802.11b/g WLan
RealTek RTL8139/810x Family Fast Ethernet Nic.

i have a internet conection of 512 kps, in windows i have no problem with the conection but in ubuntu 5.10 i have only the half broadband, i mean 200 kps, so what happend.?
In ubuntu hoary 5.04 i have no problem so any suggestions? :confused:

---

### Post by sanjose on 2005-10-25
try installing **pump**, **dnsmasq** it will help a bit

***sudo apt-get install pump dnsmasq***

---

### Post by vempire on 2005-10-28
Hi I installed pump, dnsmasq but the internet still working on half broadband what can i do? any suggestions??:confused:

---

### Post by bionnaki on 2005-10-28
Edit /etc/modprobe.d/aliases file and disable ipv6:

> 
sudo gedit /etc/modprobe.d/aliases


and change alias net-pf-10 ipv6 to alias net-pf-10 off and reboot.

---

### Post by fuscia on 2005-10-28
[QUOTE=bionnaki]Edit /etc/modprobe.d/aliases file and disable ipv6:

and change alias net-pf-10 ipv6 to alias net-pf-10 off and reboot.[/QUOTE]

wow! that really works.

---

### Post by vempire on 2005-11-19
Hi i try to do Edit /etc/modprobe.d/aliases file and disable ipv6:

and change alias net-pf-10 ipv6 to alias net-pf-10 off and reboot. 
But nothing happens i still have a half broadband. More suggestions??:confused:

---

