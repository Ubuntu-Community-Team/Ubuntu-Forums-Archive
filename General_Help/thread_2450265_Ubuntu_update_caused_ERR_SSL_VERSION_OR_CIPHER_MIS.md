---
title: "Ubuntu update caused ERR_SSL_VERSION_OR_CIPHER_MISMATCH"
date: 2020-09-10
forum: General Help
---

### Post by dreamxr on 2020-09-10
I recently updated Ubuntu Budgie using apt and the hosting site 000webhost.com is now broken for me on every browser. I get an error message:

"err_ssl_version_or_cipher_mismatch"

I used an SSL/TLS checker and found that the files.000webhost.com domain uses TLS 1.2 and not 1.3, but it used to work. Now it seems that I cannot connect to any site that doesn't have TLS 1.3 enabled and I cannot seem to find a workaround or fix for it.

Please help![COLOR=#5F6368][FONT=sans]

Edit: I have tried reinstalling Chrome, I have tried disabled QUIC protocol, clearing cache and data, proxy settings etc. Nothing worked.[/FONT][/COLOR]

---

### Post by dreamxr on 2020-09-12
Fixed.

---

