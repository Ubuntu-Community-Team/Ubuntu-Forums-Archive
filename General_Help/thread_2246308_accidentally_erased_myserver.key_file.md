---
title: "accidentally erased myserver.key file"
date: 2014-09-29
forum: General Help
---

### Post by bphillips2 on 2014-09-29
I was trying to diagnose an SSL issue when I inadvertently erased my myserver.key file at the /etc/ssl directory.  And, of course, I didn't make a backup.  I know, I'm an idiot.  Is there a way to recover the file or create a new one?

---

### Post by adriancohea on 2014-09-29
If this is what I think it is (you deleted your RSA or ECDSA private key), you're totally screwed. As in, you need to generate a new key and certificate request. Hopefully, you can get in touch with customer support for your certificate authority and get them to sign your new CSR without charging you for a whole new certification.

Good luck. :(

*hugs*

---

### Post by bphillips2 on 2014-09-29
Ok, well then maybe that's actually not so bad.  I think I can just reissue a new certificate from the certificate authority. I was actually in the process of doing that when this all happened because of another issue.

Thanks for the reply.  I'll go that route and see if it works.

---

### Post by adriancohea on 2014-09-29
Well, you would probably use openssl to generate a new certificate request and send it to them. If you didn't before, I would actually recommend taking the time to learn how to generate an ECDSA key.

---

