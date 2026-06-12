---
title: "Mutt + TLS/SMTP"
date: 2008-04-27
forum: General Help
---

### Post by pyre on 2008-04-27
What is the best way to get TLS working with self-signed certificates?  One thing that I've yet to find with many solutions that use SSL certs (even for POP or IMAP) is something that will allow me to verify the certificate against a known certificate.  For some certificates, I'll just download a known good copy of it, and then store it in ~/.msmtp/certs or ~/.certs/certificates (or something).

What I want is for one of these programs to check the cert that it gets against the cert that I downloaded.  Instead, most of these programs want a certificate that is signed by a CA or give the option to turn off certificate verification altogether (if it even allows the option to disable this).

Why isn't there a program out there that will just allow me to verify it against a known good copy of the cert?  That would surely prevent MitM attacks (Please don't tell me that someone could change the cert that I downloaded after the fact, because if someone has that kind of access there's no real point).  As it is the only way to try and prevent MitM attacks on an untrusted local network is VPN or SSH tunneling out of the local LAN (obviously there would be the potential for MitM attacks between the VPN/SSH exit node and the destination server though).

---

