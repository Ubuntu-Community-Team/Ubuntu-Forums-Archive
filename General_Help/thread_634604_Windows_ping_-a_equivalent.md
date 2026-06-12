---
title: "Windows ping -a equivalent?"
date: 2007-12-07
forum: General Help
---

### Post by Farenheit on 2007-12-07
In Windows, you can type "ping -a IP_Address" from the command prompt and it will resolve the IP to a hostname.  Is there a way to do this in Linux/Ubuntu?  Thanks!

---

### Post by anubhavrocks on 2007-12-08
You can use the host command .For example 
```
cody@shiverpool:~ > host 91.189.94.158
158.94.189.91.in-addr.arpa domain name pointer arctowski.canonical.com.
```

---

### Post by PmDematagoda on 2007-12-08
Go to System>Administration>Network Tools and go to the Whois tab, then enter the IP address, that will also work.

---

### Post by Farenheit on 2007-12-08
> You can use the host command .For example

BRILLIANT!

> Go to System>Administration>Network Tools and go to the Whois tab, then enter the IP address, that will also work.

BRILLIANT!

---

