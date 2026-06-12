---
title: "DNS Server"
date: 2005-09-05
forum: General Help
---

### Post by nmarmol on 2005-09-05
Hi,

I'm having problem installing a dns in my intranet.  When I executed the command
nslookup Titan, Titan is my server, it report a problem

;; Connection timed out; no server could be reached.

Can anyone help me?

Can anyone send me a configuration file of this service?

Best Regards
nmarmol

---

### Post by nocturn on 2005-09-06
Have you set up a DNS server?

If not, you can use the hosts file, just specify titan in /etc/hosts

---

### Post by nmarmol on 2005-09-08
OK.  My dns server is running fine on my server.  But, when I coonect an windows xp client to my dns it resolve the name of my server.

nslookup titan.com  it work ok.

but when i try to resolve a name of another windows xp client in my network from another windows xp client, for example "c:\ ping -a 94.5.9.220" it take a lot of time to response and not display the name of the machine.

can anyone give me an idea what append with my dns?

all the information i searched on the net referred to an internet domain server not an intranet.

Has anyone configured dns server to an intranet?

Help please  ](*,) 

Best regards
nmarmol

---

