---
title: "SSl certification not working"
date: 2020-02-09
forum: General Help
---

### Post by cearlp2 on 2020-02-09
I completed all steps in the article [https://hostadvice.com/how-to/configure-apache-with-tls-ssl-certificate-on-ubuntu-18/]("https://www.ssldragon.com/blog/how-to-install-an-ssl-certificate-on-ubuntu/") after having already obtained the certificate and key files.
I edited the sites-enabled file default-ssl.conf and the apachectl -t showed Syntax OK. Thinking that things were copacetic I tried the [https://domain-name](https://domain-name) but nothing happened.
Where can I look to narrow down what I did wrong?

---

### Post by eyetinatim on 2020-02-10
Can you be more specific? Like what browser you are using, where did you get the SSL? What exactly error you are facing?

---

### Post by cearlp2 on 2020-02-10
I use both Safari and Firefox browsers.The certificate is a PositiveSSL certificate issued by Sectigo Certification Authority and was purchased through Namecheap.
The error is that after installing the SSL certificate on Ubuntu 18.04 and getting a Syntax OK from testing the default-ssl.conf file typing [https://'domain-name](https://'domain-name)' in either browser nothing happens. 
The 'trying' indicators of the browsers just keep trying.
Of I type the domain-name without the https:// I get a result with the lock icon showing unlocked.

---

### Post by TheFu on 2020-02-10
Please post the apache config file wrapped in code tags.  Less descriptions, more facts.  I don't use apache or I'd one of post mine. Sorry.

---

### Post by cearlp2 on 2020-02-10
Which apache config file? the ssl config files- default and default-ssl - or the apache2.conf file or all of therm?

---

