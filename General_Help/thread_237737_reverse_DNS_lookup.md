---
title: "reverse DNS lookup?"
date: 2006-08-16
forum: General Help
---

### Post by njzillest on 2006-08-16
How can i do a reverse DNS lookup?

And

Is BASH's netstat the same as DOS's netstat?


THanks

---

### Post by Bagnaj97 on 2006-08-16
To do (reverse) DNS lookups use the host command. Open a terminal and type host followed by the IP address or the domain name.

---

### Post by rbmorse on 2006-08-16
As an aside, there a whole bunch of neat DNS related utilites here:

[http://www.dnsstuff.com/](http://www.dnsstuff.com/)

---

### Post by arkham on 2006-08-16
There is also the old reliable 'nslookup' command, and for some more detailed info, you can also try using the 'dig' command and finally for even more info you can try the 'whois' command :)

---

### Post by Riverside on 2006-08-16
> **arkham said:**
> There is also the old reliable 'nslookup' command, and for some more detailed info, you can also try using the 'dig' command and finally for even more info you can try the 'whois' command :)nslookup is now deprecated, and whois won't provide information concerning rDNS PTR resource records.

Dig can provide high levels of detail, albeit needs to be used with the -x flag to perform rDNS lookups.  When troubleshooting DNS issues, the +trace flag can be very useful as it shows the full delegation path, from root name servers downwards.

For example:

anthony@catfish:~$ dig -x 82.211.81.186 +trace

; <<>> DiG 9.3.2 <<>> -x 82.211.81.186 +trace
;; global options:  printcmd
.                       517468  IN      NS      A.ROOT-SERVERS.NET.
.                       517468  IN      NS      B.ROOT-SERVERS.NET.
.                       517468  IN      NS      C.ROOT-SERVERS.NET.
.                       517468  IN      NS      D.ROOT-SERVERS.NET.
.                       517468  IN      NS      E.ROOT-SERVERS.NET.
.                       517468  IN      NS      F.ROOT-SERVERS.NET.
.                       517468  IN      NS      G.ROOT-SERVERS.NET.
.                       517468  IN      NS      H.ROOT-SERVERS.NET.
.                       517468  IN      NS      I.ROOT-SERVERS.NET.
.                       517468  IN      NS      J.ROOT-SERVERS.NET.
.                       517468  IN      NS      K.ROOT-SERVERS.NET.
.                       517468  IN      NS      L.ROOT-SERVERS.NET.
.                       517468  IN      NS      M.ROOT-SERVERS.NET.
;; Received 478 bytes from 127.0.0.1#53(127.0.0.1) in 4 ms

82.in-addr.arpa.        86400   IN      NS      NS3.NIC.FR.
82.in-addr.arpa.        86400   IN      NS      SEC1.APNIC.NET.
82.in-addr.arpa.        86400   IN      NS      SEC3.APNIC.NET.
82.in-addr.arpa.        86400   IN      NS      SUNIC.SUNET.SE.
82.in-addr.arpa.        86400   IN      NS      NS-PRI.RIPE.NET.
82.in-addr.arpa.        86400   IN      NS      TINNIE.ARIN.NET.
;; Received 287 bytes from 198.41.0.4#53(A.ROOT-SERVERS.NET) in 105 ms

81.211.82.in-addr.arpa. 172800  IN      NS      ns1.mnet.net.uk.
81.211.82.in-addr.arpa. 172800  IN      NS      ns2.mnet.net.uk.
;; Received 91 bytes from 192.134.0.49#53(NS3.NIC.FR) in 34 ms

186.81.211.82.in-addr.arpa. 86400 IN    PTR     ohiggins.ubuntu.com.
81.211.82.in-addr.arpa. 86400   IN      NS      ns1.mnet.net.uk.
81.211.82.in-addr.arpa. 86400   IN      NS      ns2.mnet.net.uk.
;; Received 156 bytes from 62.140.195.84#53(ns1.mnet.net.uk) in 29 ms

---

