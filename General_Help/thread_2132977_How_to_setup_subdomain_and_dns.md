---
title: "How to setup subdomain and dns"
date: 2013-04-06
forum: General Help
---

### Post by rxlord on 2013-04-06
hey i am running webmin to admin my server and i have a dynamic ip and i use dyndns.org for my dynamic dns service.
i have a domain gamerzforhell.cu.cc.
what i want to do is to create a subdomain for it.
i have a dynamic ip
i have bind dns server installed but it is not setted up for the domain

can anybody help me set up bind for my domain (gamerzforhell.cu.cc) on my dynamic ip (i use dyndns).I cant use 'A' record in webmin as i have a dynamic ip.
and create a subdomain eg:-  rage.gamerzforhell.cu.cc

---

### Post by savi3000 on 2013-04-06
Assuming your dynamic ip is alpha-numeric, you could setup a CNAME record.

---

### Post by rxlord on 2013-04-06
a step by step tutorial on setting up dns server on dynamic ip and creating subdomains in webmin will be great

---

### Post by Azrayal on 2013-04-06
Hi,

Take a look here: [http://doxfer.com/Webmin/BINDDNSServer](http://doxfer.com/Webmin/BINDDNSServer) 

Read the section on webmin and wilcards, you need to enable this within webmin to allow for *.domainname.com 

Thanks

---

### Post by rxlord on 2013-04-07
sorry but i watched this before but i couldnt understand.
i have a domain gamerzforhell.cu.cc and i added my dyndns domain in its cname record
As i have dynamic ip i couldnt find a tutorial on bind dns setup on dynamic ip and how to add subdomain.
I couldnt understand the above guide so plz anybody help me by explaining it for a dynamic ip.

---

### Post by dcstar on 2013-04-07
> **rxlord said:**
> hey i am running webmin to admin my server and i have a dynamic ip and i use **dyndns.org for my dynamic dns service**.
i have a domain gamerzforhell.cu.cc.
what i want to do is to create a subdomain for it.
........

Bad luck, DYDNS are the ones that host the DNS records and you have not control over what is there, only the IP address that it points to.

**You** only get to set up subdomains on DNS servers that **you** control.

Go into the DYDNS site and see if they provide subdomains.

---

### Post by rxlord on 2013-04-07
but i am using dyndns to update my ip to the domain and i have installed bind on my server.
I just wanna use the dyndns domain for cname record.Cant i do this?

---

### Post by dcstar on 2013-04-07
No.

---

### Post by efflandt on 2013-04-07
I have never used dyndns, so I am not sure how they set it up.

When I used no-ip.com for dynamic DNS they either automatically included a wildcard to make subdomains, or at least gave you that choice. I used that to just make up subdomain names on the fly to learn how to do name based virtual web hosting.

---

### Post by rxlord on 2013-04-07
can somebody then give me a link of dynamic dns website which is free and provides dns service in which i can create subdomains.Allfor free and fast

---

