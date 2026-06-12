---
title: "SSL_ERROR_RX_RECORD_TOO_LONG and ERR_SSL_PROTOCOL_ERROR ?"
date: 2019-05-20
forum: General Help
---

### Post by jskarp on 2019-05-20
Hi,

I'm fairly new to Ubuntu/Apache/SSL/Letsencrypt so please bear with me.

Our site gets SSL_ERROR_RX_RECORD_TOO_LONG in Firefox and ERR_SSL_PROTOCOL_ERROR in chrome. Google also says it is compromised and probably has been hacked. The site worked yesterday. I do not know if it has been hacked or not, but I have restored a three week old backup (including OS, am using Digital Ocean) and updated all the packages on that and all the site core, theme and plugins (wordpress unfortunately). Still the same error messages. 

My question is - how do I double check that the SSL is properly setup so I can focus on getting Google to understand it's not hacked anymore?

What steps can I take to verify that the SSL is OK server wise? (SSL Labs says OK, A grade)

The site is eclife.se
Using Ubuntu 18.04.2

---

### Post by dino99 on 2019-05-20
I cant help on that case, but i can grab some info around the error outputs, like:
[https://www.thesslstore.com/blog/ssl_error_rx_record_too_long/](https://www.thesslstore.com/blog/ssl_error_rx_record_too_long/)

---

### Post by jskarp on 2019-05-20
Yes, I encoutered that earlier but need more specific help unfortunately. The weird thing, the configuration I used three weeks ago in the backup was fine and since the possible attack was more recently, why is the backup not working?

---

