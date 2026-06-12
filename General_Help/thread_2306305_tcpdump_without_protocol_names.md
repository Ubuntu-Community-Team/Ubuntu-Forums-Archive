---
title: "tcpdump without protocol names"
date: 2015-12-14
forum: General Help
---

### Post by Drenriza on 2015-12-14
Hey all

How do you get tcpdump to omit the protocol names and print the port numbers directly?

> -n     Don't convert addresses (i.e., host addresses, port numbers, etc.) to names.
-n does not work

Thanks in advance
Kind regards

---

### Post by HermanAB on 2015-12-14
I normally use something like this: 
tcpdump -nXl -i eth0 

More here:
[http://www.aeronetworks.ca/2014/03/network-debugging.html](http://www.aeronetworks.ca/2014/03/network-debugging.html)

---

### Post by Doug S on 2015-12-14
> **Drenriza said:**
> -n does not workShow us an example. I have never known the -n option not to work as expected.

---

