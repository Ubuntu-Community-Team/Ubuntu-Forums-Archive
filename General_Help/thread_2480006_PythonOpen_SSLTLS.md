---
title: "Python/Open SSL/TLS"
date: 2022-10-15
forum: General Help
---

### Post by zathrusuk on 2022-10-15
Hi i use flexget (via python) which accesses an old server that uses a week key, under 20.04 i updated OpenSSL.Conf with the settings below to get around the 

openssl_conf = default_conf

[ default_conf ]
ssl_conf = ssl_sect

[ ssl_sect ]
system_default = system_default_sect

[ system_default_sect ]
MinProtocol = TLSv1.1
CipherString = DEFAULT@SECLEVEL=1 

The error (DH_KEY_TOO_SMALL), having updgrade to 22.04.01, the same settings don't appear to be working. Can any one offer any suggestions?

Thanks

Mike

---

