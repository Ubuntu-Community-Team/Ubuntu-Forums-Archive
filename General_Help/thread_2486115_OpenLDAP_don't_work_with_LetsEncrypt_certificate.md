---
title: "OpenLDAP don't work with LetsEncrypt certificate"
date: 2023-04-20
forum: General Help
---

### Post by tuxor2 on 2023-04-20
Hi,


I’m working on openldap and I want to secure it with a LetsEncrypt certificate. Certbot ends OK and my certificate works well on nginx.


I install openldap-2.5.14 from sources with the configure option "--with-tls=openssl" and everything seems OK.


First, I start slapd.service with a light slapd.conf (without SSL configuration) and it’s ok, I can connect my directory.


In a second step, i add the SSL configuration :
```
TLSCACertificateFile /pki/chain.pem
TLSCertificateFile /pki/cert.pem
TLSCertificateKeyFile /pki/privkey.pem
TLSVerifyClient try
```

I launch slapd in debug mode (no slapd.service)
```
/usr/sbin/slapd -g ldap -u admldap -f /etc/openldap/slapd.conf -n slapddata -d -1
```

and it return this error :
```
6441646b.3646de80 0x7f91695f7940 TLS: could not use CA certificate file `/pki/chain.pem': Error while reading file. (-64)
```


What i don't understand is if i put a wrong filename in TLSCACertificateFile, i obtain the same error message. So i think the error don't come with the CACert contain, but with access to the file. I put openldap:ldap in owner/group of my PEM files, but nothing works.
```
644164a7.13bd3adb 0x7fe3f4988940 TLS: could not use CA certificate file `/pki/toto.pem': Error while reading file. (-64)
```


An idea would be welcome.


Sincerely

---

### Post by tuxor2 on 2023-04-20
EURÊKA

I like so much ask a question and find the answer myself......



I downloaded the **[LetsEncrypt root certificate]("https://letsencrypt.org/certs/isrg-root-x1-cross-signed.pem")** and concat it with my own **cert.pem** from LetsEncrypt and all seems works.

```
cat root.pem cert.pem >> CA.pem
```

---

### Post by tuxor2 on 2023-04-24
UP.

After more tests, my certificate CA.pem isn't complete and send an error in SSL verification.


EXPLAiNATION
The fullchain.pem contain all the necessary certificate chain but not in the good order (server > intermediate > root).


SOLUTION :
In my last tests, i isoled the intermediate certificate of the fullchain.pem (between the root and server cert) in a intermediate.pem file and make my own "fullchain" in the order (root > intermediate > server) :

```

root# > CA.pem
root# cat root.pem intermediate.pem cert.pem > CA.pem

```

and add it to TLSCACertificateFile in slapd.conf


Hope this helpfull.

Best regards

---

