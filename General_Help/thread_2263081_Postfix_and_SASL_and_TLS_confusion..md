---
title: "Postfix and SASL and TLS confusion."
date: 2015-01-29
forum: General Help
---

### Post by NertSkull on 2015-01-29
Here's my basic question:

How can a self-generated, self-signed OpenSSL certificate be used to encrypt my connection to a SMTP provider?  Don't I need their public key? Or they need mine? Or something along those lines? It makes no sense to me. 

Details:

I've been setting up postfix to act as a smtp relay to my website that is using Zoho mail as the main email provider. I want postfix to handle the phpmailer requests from my website, and send them on to the Zoho servers. This way I get a copy of the sent email in the zoho 'sent mail' folder. 

I set up a relay_map and my sasl_paswd file and the hashes, and they seem to be okay. 

(As an aside, let me say I have no clue what the sasl is doing, I know it is something about authenticating me on 'their' network, but I don't get it. My current 'idea' is its basically 'the protocol to login to zoho')

Anyway, that didn't work. I was getting TLS failures, so reading more, I realized I needed a TLS Cert to login. Makes sense.  

But I just created the private key and the certificate on my computer. And then I signed it myself.  I ran this command:

```
openssl req -x509 -sha256 -newkey rsa:256 -keyout smtpd_private.pem -out smtpd_cert.pem -days 3650
```

I then also ran this command to create a decrypted version of the key

```
 openssl rsa -in smtpd_private.pem -out smtpd_private_decrypted.pem 
```

I then added the following lines to my main.cf in postfix

```

smtpd_tls_security_level=encrypt
smtp_tls_security_level=encrypt


smtpd_tls_cert_file=/etc/postfix/ssl_certs/smtpd_cert.pem
smtpd_tls_key_file=/etc/postfix/ssl_certs/smtpd_private_decrypted.pem

#SASL stuff below here

```

At this point, it appears to work. I don't know how or why, but I can send emails. And the emails show up in the 'sent mail' folder of my Zoho account. I have the port set to 587, so I assume that is 'forcing' me on the TLS stuff. I check headers of mail I receive, and they come from the Zoho mail.

As far as I can tell, I'm logging in, WITH TLS encryption to my SMTP account at Zoho, and then relaying the mail on from there.

But how can that be. I have no private or public key from them. They shouldn't have any private or public key from me. I generated the certificate solely on my computer. How can the set up an asymmetric encryption?

I'm sure this is a basic question for other, but I've discovered that Email and SMTP servers and postfix and all things related to that world are crazy confusing to me

......

Also, in addition to that, if anyone sees that I'm doing something stupid with this setup, please let me know. This is my first foray into postfix.

---

