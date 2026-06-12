---
title: "Apache2 and PEAR packages"
date: 2007-07-06
forum: General Help
---

### Post by darkdigger on 2007-07-06
Hi everyone,
I'm running a Feisty LAMP server and I'm working on a website that needs to use the HTTP_Request extension to make a POST to another server and get a response back. I installed the **php-http-request** and the **php-http** packages using apt-get and restarted my apache2 server, but whenever I try to use the **HTTP_Request** extension, php gives me the error:

```
Fatal error: Class 'HTTP_Request' not found in /www/usc_collegiateenterprises/checkout/index.php on line 24
```

I tried ugprading the pear installation using *pear upgrade-all* and that successfully completed, but Apache2 (after apache restart) still can't find the class. I suspect PHP isn't loading the library properly/at all.

If anybody has any info on this, I'd be thrilled for tips. Maybe there's another extension to use for POSTing?

Best,
Arash

---

### Post by darkdigger on 2007-07-06
I kept messing around with it and ended up using the **php5-curl** package instead. It works like a charm. :)

-Arash

---

