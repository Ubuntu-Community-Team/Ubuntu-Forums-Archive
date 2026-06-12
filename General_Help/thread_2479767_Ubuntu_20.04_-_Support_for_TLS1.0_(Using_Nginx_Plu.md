---
title: "Ubuntu 20.04 - Support for TLS1.0 (Using Nginx Plus)"
date: 2022-10-06
forum: General Help
---

### Post by dblackburn123 on 2022-10-06
Hi 

We have a requirement for one of our services to support TLS1.0. We are using Nginx Plus on Ubuntu 20.04.
I have tried updating openssl.conf to include -
[I]openssl_conf = default_conf

[/I]*[default_conf]*
*ssl_conf = ssl_sect*

*[ssl_sect]*
*system_default = system_default_sect*

[I][system_default_sect]
MinProtocol = TLSv1[/I]
*CipherString = DEFAULT@SECLEVEL=1*

And then the nginx configuration includes the following for this particular proxy -
*ssl_protocols TLSv1 TLSv1.1 TLSv1.2;*
*ssl_ciphers "EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDH:@SECLEVEL=1";*

Is there anything in Ubuntu 20.04 which has now restricted the use of TLS 1.0, even if the above configuration is updated?

I understand I shouldn't be using TLSv1 but I have a requirement that is not going away for a particular client.

Thanks in advance

---

### Post by TheFu on 2022-10-06
We don't use any LTS older than v1.3 here. Sorry.  v1.2 is known to have been cracked by some govts.  Your client is definitely bucking the "better security" trend, unless they intend to have the traffic intercepted and read .... which is fine.  I'd say to load up an unpatched 16.04 server and go for it.

---

