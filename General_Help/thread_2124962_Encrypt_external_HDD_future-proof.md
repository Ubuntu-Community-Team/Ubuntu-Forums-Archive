---
title: "Encrypt external HDD: future-proof?"
date: 2013-03-12
forum: General Help
---

### Post by MrsUser on 2013-03-12
I have a new external 3TB hdd which I want to format in ext4. In 'Disks' I can choose to encrypt the hdd. 99.99% of the time I don't take my external hdd anywhere else than the next room. But I'd feel safer encrypting it still. Not sure yet to do it. However, just out of curiosity, I wonder what will happen for future updates of Ubuntu if I choose to encrypt the external hdd. Is it possible that there might be any compatibility issues or is it safe to encrypt? Also, what happens if I plug such drive in when under Windows 7? I want to avoid at any cost that the file system gets corrupted.

---

### Post by cool110 on 2013-03-12
Disk encryption uses the LUKS standard which is widely supported by most  Linux distros and should not have any future compatability issues.  Windows does not support LUKS or ext4 (unless third party software and  drivers are installed) and will not do anything to the drive.

---

### Post by MrsUser on 2013-03-12
Thank you!

---

