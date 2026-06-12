---
title: "Installing 509 certificate in ubuntu"
date: 2016-08-03
forum: General Help
---

### Post by saskiller2 on 2016-08-03
Hi all, I need to install this x.509 certificate ASAP, but my instructions don't tell me how to do the install itself. I've looked at old threads, resources from all over and nothing has helped. It is the digicert CA certificate. I'm not installing it on a server so the instructions they have are not useful. Running the most current version of Ubuntu.

I've downloaded the certificate and used openssl to convert the .crt to .pem and ran the update-ca-certificate command but that didn't seem to do anything, all the other certificates in the cert folder show up in blue.

---

### Post by gordintoronto on 2016-08-04
Have you tried putting the certificate in /etc/ssl

It's not obvious to me why a non-server would need an x.509 cert.

---

