---
title: "Problems with home directory encryption"
date: 2021-01-09
forum: General Help
---

### Post by lelolelo on 2021-01-09
I'm having a problem with the home directory encryption. When I try to connect to this computer via SSH the home directory is encrypted till I logout as it is supposed to be, but when someone physically logs in this computer the home directory stays unencrypted even after logging off. Once someone logs in physically then everyone can log in remotely or other users with admin can access the home directory without the need to decrypt the home directory because it stays unencrypted. Is there a way to force the system to encrypt the home directory again every time all user sessions logout?

---

### Post by HermanAB on 2021-01-10
You need to understand how file system encryption works.  In general, it protects data at rest, that is, when the machine is switched off.  It doesn't provide protection while the machine is running. If someone would steal the machine and sell it on Ebay, then your data will be safe.

That being said, it is generally better to encrypt the 'whole disk' and leave only a small /boot area in plain text, so that the machine can start up.  The reason is that if you only encrypt the home directory, then while the machine is operating, some bits and pieces of data could be written in unencrypted areas of the disk such as /tmp and /swap - and that is best avoided.

---

