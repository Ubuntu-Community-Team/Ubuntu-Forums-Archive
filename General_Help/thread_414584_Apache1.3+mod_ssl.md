---
title: "Apache1.3+mod_ssl"
date: 2007-04-20
forum: General Help
---

### Post by endfx on 2007-04-20
I'm having problems getting Apache1.3 working with mod_ssl.
I've installed Apache1.3, and it's working fine.

Then I've installed libapache-mod-ssl.

I've created keys:
openssl genrsa -out hostname.key 1024
openssl req -new -key hostname.key -out hostname.csr
openssl x509 -req -days 365 -in hostname.csr -signkey hostname.key -out hostname.crt

Now I've modified /etc/apache/httpd.conf:
#port 80
port 443
#listen 80
listen 443

And I've added the lines:
SSLCertificateFile /etc/apache/ssl/hostname.crt
SSLCertificateKeyFile /etc/apache/ssl/hostname.key


Then restart apache:
/etc/init.d/apache restart

Now when I try to goto my server with a webbrowser I get the following error:
192.168.0.101 has sent an incorrect or unexpected message. Error Code: -12263

Does anybody have any ideas as to what I'm doing wrong?
Thanks.

---

