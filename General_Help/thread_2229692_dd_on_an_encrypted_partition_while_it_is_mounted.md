---
title: "dd on an encrypted partition while it is mounted"
date: 2014-06-14
forum: General Help
---

### Post by Blutkoete on 2014-06-14
Hello,

this is a short question:

If I encrypt a partition and mount it providing the key, and afterwards use dd to copy blocks from that partition, will they be encrypted or unencrypted?

On the one hand, the encryption should be transparent, resulting in an unencrypted image, but on the other hand, dd uses raw access, so it might bypass the transparent decryption layer alltogether, giving me an encrypted image.

Thank you very much,

Blutkoete

P.S.: Possibility 3: The unencrypted partition is something virtual in my file system, so the result depends on whether I dd from the real physical partition or from that virtual unencrypted one.

---

