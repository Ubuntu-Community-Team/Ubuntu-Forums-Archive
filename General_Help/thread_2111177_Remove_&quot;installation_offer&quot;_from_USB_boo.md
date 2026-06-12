---
title: "Remove &quot;installation offer&quot; from USB boot"
date: 2013-02-01
forum: General Help
---

### Post by dervilo on 2013-02-01
Hi friends!

I have Ubuntu installed in the company PC and installed ubuntu-studio in a 8 Gib Pendrive, for personal use.

Every time I start from Pendrive, the computer ask me for install in the machine, what is not possible since it is a company computer.

How can I modify the Pendrive startup in order to boot direct instead to ask me for install?

Thank you so much,

Dervilo

---

### Post by C.S.Cameron on 2013-02-01
Following works for a Persistent install:

 Enter the syslinux directory, (or for UNetbootin the root directory).
    Make the syslinux.cfg file writeable
    Replace the contents of the file syslinux.cfg with:

   ```
 default persistent
    label persistent
      say Booting a persistent Ubuntu Studio session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

---

