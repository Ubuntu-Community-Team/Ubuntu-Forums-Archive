---
title: "update manager problem"
date: 2007-04-23
forum: General Help
---

### Post by Balinsky on 2007-04-23
my update manager sees the updates i need put when i try to install them i get the following error
```

W: Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/d/dpkg/dpkg-dev_1.13.24ubuntu6_all.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-15.27_i386.deb
  MD5Sum mismatch

```

any ideas?

jebsky

---

### Post by lonniehenry on 2007-04-23
You can get rid of the message by:

sudo gedit /etc/apt/sources.list

find the line for the cd and place a # in front of it. You should no longer see the message.

---

