---
title: "GUFW stopping Wireless Printer Discovery"
date: 2018-04-12
forum: General Help
---

### Post by Quarkrad on 2018-04-12
Having on and off problems seeing hp wireless printer - sometimes it prints (can see printer) sometimes no printing (printer not connected).  I'm using a static ip address for the printer.   Just run hplip-3.18.3 and when it comes to discovering the printer (manual search for 192.168.1.4) I'm told **HPLIP cannot detect printers in your network**.   If I turn my firewall off (I use GUFW as I'm not skilled in the terminal config of iptables) hp-setup can see my printer and all is well - if I turn my firewall on HPLIP cannot see anything. Any advise on how to configure GUFW or terminal command would be most appreciated. (Slightly off topic - I also need help with gufw so filezilla works on my local network.  When I would to talk to my set-top box I have to turn off my firewall).

---

### Post by kenj69 on 2018-06-05
1st solution: If your computer is behind a firewalled router then you may not have to have the computer firewall turned on. In gufw just turn Status: OFF. 

2nd solution: Add Rules in gufw for "Scanner." That is what worked for me, allowing me to leave the firewall turned on. The scanner needs Port 8612 In to work.

-=Ken=-

---

