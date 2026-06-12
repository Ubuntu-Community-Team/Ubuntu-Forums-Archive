---
title: "Error when i tried to use  &quot;openssl req&quot;  to generate keys."
date: 2019-01-15
forum: General Help
---

### Post by iPhilip on 2019-01-15
```

$ openssl req -new -x509 -newkey rsa:2048 -keyout MOK.priv -outform DER -out MOK.der -nodes -days 36500 -subj "CN=VMware/"

===========================================
 Generating a 2048 bit RSA private key
............+++
.......................+++
writing new private key to 'MOK.priv'
-----
problems making Certificate Request
===========================================
```

---

