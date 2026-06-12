---
title: "port 445"
date: 2005-06-30
forum: General Help
---

### Post by soonindallas on 2005-06-30
Hi all.

I was using ethereal today, trying to troubleshoot something.  I am usually on a cable network behind a Netgear wireless router.  Anyway I had ifdown'd my eth1 and ifup'd my eth0, I was connected via a lan cable to the cable modem.

Ethereal showed some activity on port 445, which is unfamiliar to me.  I was especially interested by the information "microsoft-ds", as there is not much of that on this box!

It seems this is something to do with Samba.

Can anyone please tell me what is occurring here and if it is dangerous.

Along the same lines, what are the periodic NBNS queries my box makes to my router (as DNS) and PTR in-addr.arpa ?

any pointers are welcome.

---

### Post by dwshard on 2007-05-17
If you are using Samba it is likely that the traffic on this port is related to Active Directory and windows Shares. Although according to Wikipedia there are some worms associated with the port (the ones listed are windows vulnerabilities as far as I know, correct me if I am wrong though).

[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers]("http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers")

---

