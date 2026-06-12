---
title: "connect to proxy server"
date: 2012-12-13
forum: General Help
---

### Post by danelwillis on 2012-12-13
I'm trying to connect to a school proxy via my laptop using Ethernet but i cant use the internet on the laptop for terminal or anything other than Firefox because i can edit the the proxy setting how to i connect my laptop to the proxy server using terminal so i can use the internet through it? I'm using backtrack kde 10.10.

---

### Post by Ms. Daisy on 2012-12-13
Which applications specifically (in terminal or otherwise) are you trying to use?

---

### Post by Rexilion on 2012-12-14
I think you either have to:

- do transparent proxying (t-proxy) with iptables
- find the proxy settings window in KDE (for QT and KDE apps)
- Ubuntu also has environment variables called http_proxy, ftp_proxy etc

---

