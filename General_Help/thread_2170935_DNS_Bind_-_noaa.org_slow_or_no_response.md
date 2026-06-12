---
title: "DNS Bind - noaa.org slow or no response"
date: 2013-08-28
forum: General Help
---

### Post by ronbaechle on 2013-08-28
Hello, running   Debian 5 Lenny.  Bind 9.5.1-P3
Per the subject line I either get no response or a very slow response (albeit once connected links tend to usually work)

I have no issue via browser connecting to this site outside of our work network.  I thought it might be related to an internal proxy but once I eliminated that I still have the same issue.

What is the best way to troubleshoot this or work around the problem.

using dig and nslookup from the dns server usually responds quick but I do sometimes see problems when testing weather.gov (I believe part of noaa).  

nslookup weather.gov
;; Got recursion not available from x.x.x.x (2nd dns), trying next server
server: x.x.x.x (windows dns server)
address x.x.x.x#53
** server can't find weather.gov: MXDOMAIN

cat /etc/resolv.conf
nameserver (internal windows dns)
nameserver (linux dhcp/dns)

---

### Post by SeijiSensei on 2013-08-28
Windows has an annoying habit of caching failed DNS queries and not trying them again.  On the Windows machine, open cmd.exe from Start Menu and type "ipconfig /flushdns" to flush the cache.  What about restarting the Windows nameserver entirely?  How about reversing the order of nameservers?  Any better?  What if you make Google's 8.8.8.8 the first nameserver in your list?

I had no trouble resolving weather.gov.  My primary DNS server is a BIND machine on my local network.

---

### Post by ronbaechle on 2013-08-28
If I just wanted to put a static address what is the best way to do this.  It works if I add an entry in the host file on a local client pc but how would I do this for everyone

Can I add a static entry to the named config for an external website and also use one with wild cards since noaa has a large amount of subdomains?

---

