---
title: "Accessing an externally encrypted USB"
date: 2021-04-08
forum: General Help
---

### Post by mollie4168 on 2021-04-08
I have a USB with medical records on it that was encrypted by the provider.  I am using Disks to open it using the password that was given to me, but it is not unlocking it.  I am waiting to hear from the provider, but since this is the first time I'm opening an encrypted drive, I wanted to verify that there is nothing else I should be doing.  Is there anything else I should know?

It's not letting me post a screenshot.  It says the partitioning is Master Boot Record, and it's a JetFlash transcend USB.  The partition type is W95 FAT32 and the contents are Unkown (BitLocker 2 ) -- Locked

Thanks.

---

### Post by CelticWarrior on 2021-04-08
Bitlocker is Microsoft proprietary encryption mechanism. It isn't supported by default in any major Linux distro including Ubuntu.

This method may work but I haven't tested it: [https://www.linuxuprising.com/2019/04/how-to-mount-bitlocker-encrypted.html](https://www.linuxuprising.com/2019/04/how-to-mount-bitlocker-encrypted.html)

---

### Post by mollie4168 on 2021-04-08
That's really good to know.  In that case, I'll open it on a PC to save the trouble. Thank you.

---

