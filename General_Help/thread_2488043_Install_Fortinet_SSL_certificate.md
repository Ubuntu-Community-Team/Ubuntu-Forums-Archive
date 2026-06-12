---
title: "Install Fortinet SSL certificate"
date: 2023-06-21
forum: General Help
---

### Post by fandreani on 2023-06-21
Hi, we need to implement deep ssl inspection on all our clients but we need also to install our firewall certificate (Fortinet_CA_SSL.cer) on every local machine that we have in our organization.
Now for windows and macos the install is very simple and it works, for ubuntu i tried to convert the .cer file in .crt (openssl x509 -inform DER -in fortinet_ca_ssl.cer -out fortinet_ca_ssl.crt) , moved to /usr/share/ca-certificates and launched update-ca-certificates.
When i open my browser (chrome) everything is blocked by the Fortinet , hence the certificate hasn't been installed correctly, instead on Firefox i can import correctly the certificate.
Has anyone faced a similar situation?
I am currently using Ubuntu 22 LTS
Regards,
Federico.

---

### Post by TheFu on 2023-06-21
"Some" browsers, don't use the system SSLCert store. They have their own.  Maybe open a bug with that browser, since they should be using the system CA Cert store, but decided not to do so.  Or you could learn what they require to import the CA into their CA Cert store.

Google gave this answer: 
bout 6,220,000 results (0.49 seconds) 
Go to chrome://settings.
[LIST=1]
[*]    On the left, click Privacy and security.
[*]    Click Security.
[*]    Scroll to Advanced.
[*]    Click Manage certificates.
[*]    In the list, find the newly-added CAs.
[/LIST]
No idea if that works or not.

---

### Post by fandreani on 2023-06-22
Hi, thanks for the reply, now chrome works fine with deep inspection active !!

---

