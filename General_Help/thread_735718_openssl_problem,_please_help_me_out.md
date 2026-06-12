---
title: "openssl problem, please help me out"
date: 2008-03-25
forum: General Help
---

### Post by feelexit on 2008-03-25
[https://help.ubuntu.com/7.10/server/C/httpd.html](https://help.ubuntu.com/7.10/server/C/httpd.html)

I am following the instruction from this article, have my apache server installed and  openssl enable.

right now, 
[https://localhost/](https://localhost/)  , it works

but if i try non secure link
http//localhost/
I am getting this error message
-------------------------------
Bad Request

Your browser sent a request that this server could not understand.
Reason: You're speaking plain HTTP to an SSL-enabled server port.
Instead use the HTTPS scheme to access this URL, please.

    Hint: [https://127.0.1.1/](https://127.0.1.1/)

Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e Server at 127.0.1.1 Port 443
-----------------------------------

I checked my ports.conf file

Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>


I have mod_ssl installed , so port number got overwrited.  it kept listening port 443.  how to fix it ?

---

