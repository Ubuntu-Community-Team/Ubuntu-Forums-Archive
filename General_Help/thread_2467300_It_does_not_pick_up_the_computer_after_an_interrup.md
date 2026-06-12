---
title: "It does not pick up the computer after an interruption in the update."
date: 2021-09-22
forum: General Help
---

### Post by ahklobouk on 2021-09-22
I have version 20.04
While I was updating the computer was turned off and now it does not lift Ubuntu.

---

### Post by grahammechanical on 2021-09-22
Do you get a Grub boot menu? If you do I suggest that at the Grub boot menu you select Advanced Options for Ubuntu and then select a Linux kernel with recovery mode. At the recovery menu select Network to set up an internet connection. Then select Root - drop to root shell prompt. Then run these two commands

```
 apt update
apt upgrade
```

See if that completes the update/upgrade. To exit the root shell prompt type exit. At the recovery menu select Resume. Does that get you to the Ubuntu desktop? It will be in a basic video mode because the normal video driver was not loaded. If you get to a working desktop you can reboot and the reboot will load the normal video driver.

Regards

---

