---
title: "ssl multiple subdomains"
date: 2014-03-04
forum: General Help
---

### Post by Blisk on 2014-03-04
As I readed there is problem to have multiple ssl subdomains.
There are some solutions but didn't worked for me. I tried it.
Can someone helps me to manage this?
just like to have 3 subdomain like these.
[https://mysite.mydomain.com](https://mysite.mydomain.com)
[https://mysitetwo.mydomain.com](https://mysitetwo.mydomain.com)
[https://mysitethree.mydomain.com](https://mysitethree.mydomain.com)

I have installed lates ubuntu 12 and apache 2.

I have managed to work this out but messed with http settings so none of ordinary http didn't worked. 
[http://mysite.mydomain.com](http://mysite.mydomain.com)
[http://mysitetwo.mydomain.com](http://mysitetwo.mydomain.com)
[http://mysitethree.mydomain.com](http://mysitethree.mydomain.com)

---

### Post by Lars Noodén on 2014-03-04
From what I recall, you have to use separate IP addresses for each vhost if you are using separate certificates.  If you are using the same certificate, you could do something like this:

[https://wiki.apache.org/httpd/NameBasedSSLVHosts](https://wiki.apache.org/httpd/NameBasedSSLVHosts)

---

### Post by Blisk on 2014-03-04
I know about multiple IPs but that is not an option for me and I use the same certificate. 
I tried what was on that link but didn't woked for me....

---

### Post by Habitual on 2014-03-04
What is the nature and origin of this certificate?

---

