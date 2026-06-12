---
title: "Can't access encrypted drive after reinstall"
date: 2012-11-09
forum: General Help
---

### Post by M@s on 2012-11-09
Just made a fresh reinstall of DreamStudio 12.04, but now I can't access my encrypted drive. I'm 98% certain the password is correct, because I saved it in my password manager when I created the partition. When I try to mount it from Nautilus I get the error message:
```
Error unlocking device: cryptsetup exited with exit code 2: No key available with this passphrase.
```

It's an ext4 partition, created with the Disk Utility. I have another encrypted disk created the same way, which works.

Anything else than a wrong password that can produce this error?

---

