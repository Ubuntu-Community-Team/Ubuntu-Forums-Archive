---
title: "postfix - smtp key / smtpd.csr problem"
date: 2007-09-11
forum: General Help
---

### Post by prickly on 2007-09-11
EDIT - i misstyped the passphrase - problem solved.

I am following this guide to setup Postfix on Ubuntu server 6.06: [https://help.ubuntu.com/7.04/server/C/postfix.html](https://help.ubuntu.com/7.04/server/C/postfix.html)

At step 8 of the guide i get to this point:

openssl req -new -key smtpd.key -out smtpd.csr

I am then prompted for a passphrase after whic i get the following error:

unable to load private key
4081:error:06065064: digital envelope routines:EVP_DecryptFinal_ex:bad decrypt:evp_enc.c:454
4081:error:096A065:PEM routines:PEM_do_header:bad decrypt:pem_lib.c:425:

---

