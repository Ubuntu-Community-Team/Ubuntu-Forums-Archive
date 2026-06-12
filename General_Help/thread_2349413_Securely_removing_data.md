---
title: "Securely removing data"
date: 2017-01-14
forum: General Help
---

### Post by makem2 on 2017-01-14
I use rar with a password to save some data. When I extract that data I extract it to a ramdisk. The extracted data is removed from the ramdisk on a reboot but is not removed from the system.

When I look in the users .cache I find readable data which was viewed after the password had been used and was supposedly wiped on reboot.

Is it possible to prevent this data ever getting to the .cache during extraction to the ramdisk perhaps by using a different method?

---

### Post by TheFu on 2017-01-15
Don't use a GUI tool to access rar data.

Why not use a proper encrypted container based on dm-crypt/LUKS instead?

---

### Post by HermanAB on 2017-01-15
Encrypt your whole disk with LUKS.  This is the only way to prevent leakage of sensitive data to plain text areas.

---

