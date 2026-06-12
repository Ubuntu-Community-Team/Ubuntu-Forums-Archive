---
title: "Message about bluetooth in kernel on startup"
date: 2023-03-28
forum: General Help
---

### Post by drew1121 on 2023-03-28
Today when i booted up my computer i got the message
"Bluetooth: hci0: Failed to read codec capabilities ( -22)" on startup
It just appeared. Does anyone know why this appeared? I can can connect to bluetooth just fine. Should I be worried?

---

### Post by ActionParsnip on 2023-03-29
If you boot an older kernel, is it OK?

---

### Post by ActionParsnip on 2023-03-29
If Bluetooth works I wouldn't sweat it too much

---

### Post by MAFoElffen on 2023-03-29
Or if you boot on a newer Kernel...

There was a bad commit in Linux Kernel 5.16 that caused this message. It was corrected in Linux Kernel 5.17.
> 
8961987f3f5fa2f2618e72304d013c8dd5e604a6 is the first bad commit
commit 8961987f3f5fa2f2618e72304d013c8dd5e604a6
Author: Kiran K <kiran.k@intel.com>
Date:   Tue Sep 7 15:42:37 2021 +0530

    Bluetooth: Enumerate local supported codec and cache details
    
    Move reading of supported local codecs into a separate init function,
    query codecs capabilities and cache the data
    
    Signed-off-by: Kiran K <kiran.k@intel.com>
    Signed-off-by: Chethan T N <chethan.tumkur.narayan@intel.com>
    Signed-off-by: Srivatsa Ravishankar <ravishankar.srivatsa@intel.com>
    Signed-off-by: Luiz Augusto von Dentz <luiz.von.dentz@intel.com>

 include/net/bluetooth/hci.h      |  41 ++++++++++
 include/net/bluetooth/hci_core.h |  17 ++++
 net/bluetooth/Makefile           |   2 +-
 net/bluetooth/hci_codec.c        | 172 +++++++++++++++++++++++++++++++++++++++
 net/bluetooth/hci_codec.h        |   6 ++
 net/bluetooth/hci_core.c         |  11 ++-
 6 files changed, 244 insertions(+), 5 deletions(-)
 create mode 100644 net/bluetooth/hci_codec.c
 create mode 100644 net/bluetooth/hci_codec.h

To see if this is the case, please post the out of this, within CODE Tags:
```

uname -r

```

---

