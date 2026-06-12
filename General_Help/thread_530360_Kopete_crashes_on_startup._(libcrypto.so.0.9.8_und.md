---
title: "Kopete crashes on startup. (libcrypto.so.0.9.8 undefined symbol)"
date: 2007-08-20
forum: General Help
---

### Post by affected on 2007-08-20
Hello.
Whenever I try to start Kopete, it just crashes. This is what it outputs in console:

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kopete: ERROR: Error connecting KSSL: -1
kopete: ERROR: Communication problem with kopete, it probably crashed.
KCrash: Application 'kopete' crashing...

```

Now, the X errors are probably because I don't have my Wacom plugged in at the moment, so I'm guessing it's the SSL errors that are killing it. Any ideas how to fix this?

---

