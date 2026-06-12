---
title: "Import windows certificate"
date: 2019-10-16
forum: General Help
---

### Post by rapatel on 2019-10-16
Hello,

We have a windows PKI implementation. I have exported the Root CA and sub CA and imported them but I still keep getting error certificate verify failed, SEC_erro_unknown_issuer. What am I doing wrong. I know the certificate is valid as I don't get any errors on a windows box.

Thank you.

---

### Post by wildmanne39 on 2019-10-16
Are you trying to import it to Ubuntu? if so why?

---

### Post by rapatel on 2019-10-17
Yes, trying to import it into the Ubuntu client. I have server that has resources via https (443).

---

### Post by &amp;KyT$0P# on 2019-10-17
> **rapatel said:**
> I have exported the Root CA and sub CA and imported them 

How did you import them?

> I still keep getting error certificate verify failed, SEC_erro_unknown_issuer.

What app is giving you this error?

---

### Post by rapatel on 2019-10-17
The app is Xibo client. This is going to be for displaying digital signage.

Followed the instructions here [https://askubuntu.com/questions/73287/how-do-i-install-a-root-certificate](https://askubuntu.com/questions/73287/how-do-i-install-a-root-certificate). Snip form it below. I do see them in the certs folder located /etc/ssl/certs folder after following the instructions. I added both the root CA, sub CA and chain cert. 

Given a CA certificate file foo.crt, follow these steps to install it on Ubuntu:

  
[LIST=1]
[*]Create a directory for extra CA certificates in /usr/share/ca-certificates:
  sudo mkdir /usr/share/ca-certificates/extra 
[*]Copy the CA .crt file to this directory:
  sudo cp foo.crt /usr/share/ca-certificates/extra/foo.crt 
[*]Let Ubuntu add the .crt file's path relative to /usr/share/ca-certificates to /etc/ca-certificates.conf:
  sudo dpkg-reconfigure ca-certificates
  To do this non-interactively, run:
  sudo update-ca-certificates 
[/LIST]
  In case of a .pem file on Ubuntu, it must first be converted to a .crt file:
  openssl x509 -in foo.pem -inform PEM -out foo.crt

---

