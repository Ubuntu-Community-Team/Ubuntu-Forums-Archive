---
title: "Bit torrent (uTorrent w/wine)Help"
date: 2008-04-08
forum: General Help
---

### Post by levi007 on 2008-04-08
Hey guys.  I downloaded Bit Torrent, and uTorrent (wine), and neither one of them will connect.  I get the error "104, connection reset by peers" in bit torrent, with all the torrent files I downloaded.  Is this a networking/firewall problem, and if so, i can i fix it.  Thanks.

---

### Post by ryanhaigh on 2008-04-09
It has been a long time since I used wine and utorrent but I remember reading that the latest version may not have been compatible or something (vague memory warning). 

Have you considered using a native linux client such as deluge, tranmission or ktorrent? There is also azureus of course.

---

### Post by levi007 on 2008-04-09
I tried deluge, and still no go.  I know the trackers are working, since a buddy of mine sent me the Seed.  Limewire also doesn't want to work.

---

### Post by levi007 on 2008-04-09
IF this can help, my iptable -L  states:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
           tcp  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  


I have no clue wtf this means.  Something tells me this has to be a firewall problem though

---

### Post by ryanhaigh on 2008-04-09
Sounds like your isp might be blocking p2p traffic either by denying dns requests to the popular sites or other means. You may want to try using an alternate dns service and turning on encryption in your torrent app.

---

### Post by levi007 on 2008-04-10
For some reason it started working?  I have no clue why, but I updated some things.

---

