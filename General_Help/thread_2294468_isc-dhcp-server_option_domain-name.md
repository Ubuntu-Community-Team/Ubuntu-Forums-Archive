---
title: "isc-dhcp-server option domain-name"
date: 2015-09-11
forum: General Help
---

### Post by Drenriza on 2015-09-11
Hi all

When setting up a DHCP server we have the option to specify a domain-name through the option section.
My question is, what benefit does it have to add the DHCP service to a domain? Or for that matter include a server in a domain when installing the system?

This is a very open question that i am searching feedback for, also if you have any links for relevant blogs, articles / other i am very interested.

Thanks on advance.
Kind regards.

---

### Post by SeijiSensei on 2015-09-11
That's referring to a "domain name" in the Unix/Internet sense, like "ubuntuforums.org".  If you pass a domain name to the DHCP client, the resolver will usually append the domain automatically to "unqualified" host names like plain "www".  If you were on a machine where ubuntuforums.org was the domain name, typing "ping www" would be interpreted as "ping www.ubuntuforums.org". 

You can also specify "domain search" entries which are alternate domains to try on unqualified names.

None of this has anything to do with "domains" in the Microsoft meaning of the term.

---

### Post by Doug S on 2015-09-11
> **SeijiSensei said:**
> That's referring to a "domain name" in the Unix/Internet sense, like "ubuntuforums.org".  If you pass a domain name to the DHCP client, the resolver will usually append the domain automatically to "unqualified" host names like plain "www".  If you were on a machine where ubuntuforums.org was the domain name, typing "ping www" would be interpreted as "ping www.ubuntuforums.org". +1. Thats is exactly what I do on my LAN, and for the reasons Seiji mentions.

---

