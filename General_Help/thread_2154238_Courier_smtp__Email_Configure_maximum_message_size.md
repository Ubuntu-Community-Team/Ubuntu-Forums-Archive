---
title: "Courier smtp / Email: Configure maximum message size"
date: 2013-06-14
forum: General Help
---

### Post by scrr on 2013-06-14
I am a mailserver-newbie trying to change the default 10MB size limit in courier smtp on my server.

I think I have to create a file ```
/etc/courier/sizelimit
```

I did (in my case it only contains the string "52428800"), but the changes don't get picked up. What am I missing? 

In case it helps, here are my versions:


```
# dpkg -l | grep courier
ii  courier-authdaemon               0.63.0-4build1                  Courier authentication daemon
ii  courier-authlib                  0.63.0-4build1                  Courier authentication library
ii  courier-authlib-userdb           0.63.0-4build1                  userdb support for the Courier authentication library
ii  courier-base                     0.66.1-1ubuntu4                 Courier mail server - base system
ii  courier-doc                      0.66.1-1ubuntu4                 Courier mail server - additional documentation
ii  courier-imap                     4.9.1-1ubuntu4                  Courier mail server - IMAP server
ii  courier-imap-ssl                 4.9.1-1ubuntu4                  Courier mail server - IMAP over SSL
ii  courier-maildrop                 0.66.1-1ubuntu4                 Courier mail server - mail delivery agent
ri  courier-mta                      0.66.1-1ubuntu4                 Courier mail server - ESMTP daemon
rc  courier-mta-ssl                  0.66.1-1ubuntu4                 Courier mail server - ESMTP over SSL
ii  courier-ssl                      0.66.1-1ubuntu4                 Courier mail server - SSL/TLS Support

```

---

