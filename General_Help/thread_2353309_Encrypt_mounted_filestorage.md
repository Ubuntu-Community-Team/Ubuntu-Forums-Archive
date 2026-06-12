---
title: "Encrypt mounted filestorage"
date: 2017-02-20
forum: General Help
---

### Post by steveearle86 on 2017-02-20
Hi all,
I have some internal and external harddrives on my Ubuntu 16.10 system (additional to the system drive) I want to be able to encrpyt them so that they cannot be read if plugged into another PC, without entering the encryption key.

If possible, I would like them to be unencrypted when a given user logs into Ubuntu (rather than having the decryption as part of the boot process)
Is this possible? If so, what software would I need?
Thanks

---

### Post by HermanAB on 2017-02-20
Yes, you can encrypt them with LUKS using the cryptsetup program.

---

