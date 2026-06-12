---
title: "Update manager error"
date: 2008-06-11
forum: General Help
---

### Post by Trixilver on 2008-06-11
I get this error whenever I check for updates:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

However, updates still download and install so I have no idea what it means. Should I be worried?

---

### Post by wormser on 2008-06-11
You need to add the [Medibuntu Key]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f").

```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by Trixilver on 2008-06-11
Thanks!

---

