---
title: "whats my ubuntu IP"
date: 2005-10-28
forum: General Help
---

### Post by serlex on 2005-10-28
was going to set up vnc, but gona try shh first. installed openssh server, want to connect from university by Putty or shell

but just need my IP? or domain name, what ever its called

ipconfig eth0?

---

### Post by ronin_ar on 2005-10-28
[QUOTE=serlex]was going to set up vnc, but gona try shh first. installed openssh server, want to connect from university by Putty or shell

but just need my IP? or domain name, what ever its called

ipconfig eth0?[/QUOTE]

run: ifconfig

then you will see:

ethXXX      Link encap:Ethernet  HWaddr 00:00:00:00:00:00
              inet addr:000.000.000.000  Bcast:255.255.255.255  Mask:255.255.255.0


where 000.000.000.000 will be you ip addres.
ethXXX will be your nic, usually eth0.

Hope that helps!

---

### Post by serlex on 2005-10-28
thx for reply, i tried 192.168......... (inet addr) from another computer using Putty, using port 22. i get error :'connection refused' i got no firewalls or anything. any ideas?

---

### Post by serlex on 2005-10-28
:(, just found out what disadvantages VMware have, im use NAT to connect my virtual ubuntu to the internet. which uses the my Windows IP. need to do bridge connection!!

---

### Post by herot on 2005-10-28
type ```
nmap localhost
``` and post your output please...
i recently set my machine to accept VNC, FTP, and SSH so maybe i can help you...

---

### Post by herot on 2005-10-28
oh your running it in vmware? well, things get a little different there...
;)

---

