---
title: "DNSmasq failed to start"
date: 2007-06-18
forum: General Help
---

### Post by brobertsleo on 2007-06-18
I have installed a LAMP server on Ubuntu and was looking forward to running a DNS server using MyDNS. I installed the dnsmasq using apt-get but it gave me an error message saying that it could not bind the socket and that the address was already in use. Does anyone know what's going on?

---

### Post by zanglang on 2007-06-18
Something else is using the DNS port perhaps. Have you installed, or unknowingly installed, another DNS server package previously, for example Bind? (you can check under the package 'bind' and 'bind9')

---

