---
title: "Generat CSR Help"
date: 2022-11-12
forum: General Help
---

### Post by patdundee on 2022-11-12
Hi Guys
I am having issues with Ubuntu Server 22.04 running LAMP & Using OpenSSL version 3.0.2 from cmd line

I am trying to generate a csr and key for a geotrust cert using the normal OpenSSL command 
    openssl -help req –new –newkey rsa:2048 –nodes –keyout mydomain.key –out mydomain.csr

All it returns is 
    req: Use -help for summary
Which is not a great deal of help

What has changed since earlier version of OpenSSL? Is there a different cmd line to use now?

Many thanks

---

### Post by TheFu on 2022-11-12
Thanks to much for posting the solution!  That is extremely helpful to others in the community!

---

