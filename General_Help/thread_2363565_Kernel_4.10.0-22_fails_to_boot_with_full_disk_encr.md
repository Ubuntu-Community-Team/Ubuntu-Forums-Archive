---
title: "Kernel 4.10.0-22 fails to boot with full disk encryption"
date: 2017-06-11
forum: General Help
---

### Post by jedcred on 2017-06-11
Recently updated to kernel 4.10.0-22 via apt on Ubuntu 17.04. I use full disk encryption that I set up via the installer when I first installed 16.04. After I correctly type in the decrypt passphrase, the spinner rotates once and halts. If I press Esc before inputting the passphrase, I can see the console output. It shows various .service files listed after I decrypt the volume (I imagine from systemd), then just waits with the occasional "cpu stalled for x seconds" message. I can't seem to move on from there and the console does not accept any input.

I can, however, boot from the previous kernel version of 4.10.0-21, or the recovery version of 4.10.0-22. I've tried rebuilding the boot image, but I still cannot boot with -22. What steps can I take to further debug this issue?

Thanks!

EDIT: added attachment of console output

---

