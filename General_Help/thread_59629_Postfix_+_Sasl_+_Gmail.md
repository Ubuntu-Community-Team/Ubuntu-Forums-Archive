---
title: "Postfix + Sasl + Gmail"
date: 2005-08-24
forum: General Help
---

### Post by danielti on 2005-08-24
1) Install postfix, postfix-tls,libsasl2 ,libsasl2-modules ,sasl2-bin  

2) In /etc/main.cf add:
relay_domains = $mydestination, $mydomain, $mynetworks, xxx.xxx.xxx.xxx/xx, gmail.com
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous

tls_random_source = dev:/dev/urandom
smtp_tls_scert_verifydepth = 5
smtp_tls_CApath=/etc/ssl/certs
smtp_tls_enforce_peername = no
smtp_tls_per_site = hash:/etc/postfix/usar_tls

3) Create the file /etc/postfix/sasl_password :
smtp.gmail.com  [email]user@gmail.com[/email]:password
gmail-smtp.google.akadns.net    [email]user@gmail.com[/email]:password

4) Create the file /etc/postfix/usar_tls :
smtp.gmail.com  MUST_NOPEERMATCH
gmail-smtp.google.akadns.net    MUST_NOPEERMATCH

5) Go to  /etc/postfix as root and run:
postmap sasl_password
postmap usar_tls

Thsi will create sasl_password.db and usar_tls.db.
MUST BE IN /ETC/POSTFIX!

6) Restart postfix : /etc/init.d/postfix restart

---

