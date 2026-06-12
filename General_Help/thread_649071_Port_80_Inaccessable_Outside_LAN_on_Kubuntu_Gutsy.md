---
title: "Port 80 Inaccessable Outside LAN on Kubuntu Gutsy"
date: 2007-12-24
forum: General Help
---

### Post by cripperz on 2007-12-24
Hi guys,

its been awhile that i tried figuring out this issue. Im on Starhub Cable (SG), tested my router and settings to confirm that its not a router issue nor due to ISP blockage.

I tested Xampp on winxp and i could manage to visit my [http://traxxion.cripperz-prodigy.org](http://traxxion.cripperz-prodigy.org) with not issue. But when im Kubuntu Gutsy, where i install Apache2 / PHP / Mysql, it seems that i could not visit [http://traxxion.cripperz-prodigy.org](http://traxxion.cripperz-prodigy.org), instead i have to use [http://traxxion.cripperz-prodigy.org:8080](http://traxxion.cripperz-prodigy.org:8080) or some other ports to enable my page to be viewed.


can anyone kindly advise or share if you have similar issues. I have done some troubleshooting regards with router or ISP and its clear cut that those was not the issue. My Kubuntu does not have any firewall on, not to the extend of my knowledge as its default installed and no other firewall program is being configured yet.


Cheers guys, Kubuntu Rocks !

---

### Post by p_quarles on 2007-12-24
Out of curiosity, how long has it been since you used the XAMPP setup in Windows? Honestly, this really looks like an ISP blocking port 80. Is it possible they recently *started *doing this?

Anyway, I can suggest a few things to look at, some of which it sounds like you've already done:
1) Make sure your router is properly configured
2) Make sure /etc/apache2/ports.conf is properly configured
3) Make sure that the main interface in /etc/network/interfaces has a static IP address assigned to it
4) Doublecheck that you don't have any firewall rules related to port 80. You can check this by running:
```
sudo iptables -L
```

---

### Post by cripperz on 2007-12-24
Basically i have two machines.. assign *.100 as DMZ in the router. So i will just change to the DMZ ip to either of the machine to test. its pretty frustrating ..haha 

but like you mention, i will give it a second look at the things you highlighted. Hopefully this issue can resolve anytime soon

I will update you again. Thanks for the highlight.

---

