---
title: "Sendmail takes 60 seconds"
date: 2007-11-06
forum: General Help
---

### Post by old_mac_jeffle on 2007-11-06
Yes, I looked at the sendmail threads.

Every time I send an email w/ sendmail, it takes 60 seconds to complete. I'd rather not have to wait like that.

Ubuntu Feisty fully updated.

---

### Post by ScottCC on 2007-11-13
I had a problem with sendmail taking too long to send also.  
I ended up finding out that sendmail doesn't like unresolvable domain names.  
The real problem was this error in syslog:
"My unqualified host name (ubuntu) unknown; sleeping for retry"

I bought a cheap domain and did this at the console.

#> hostname mydomain.com

#> /etc/init.d/sendmail restart

after that things were all good.

edit: OMG I just realized that the post I replied to was 2 years old :/ doh

---

