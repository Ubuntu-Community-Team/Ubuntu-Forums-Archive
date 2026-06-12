---
title: "Prevent USB disks from dancing around on /dev/sd*"
date: 2007-05-03
forum: General Help
---

### Post by kub-fu on 2007-05-03
Hi,

I'm just a couple of weeks born Kubuntu user, and there's one small annoyance I'd love to get some help on.

I have many USB external hard drives, a memory card reader, and a couple of flash drives. Whenever I plug one in, it shows on /dev/sd*, but it's not fixed, sometimes a hard drive will get sdg, sometimes sdi, etc.

How does one assign a fixed location so I can mount those drives more quickly?

I'm on Kubuntu Feisty Fawn x64.

Thanks in advance!

---

### Post by dcstar on 2007-05-03
> **kub-fu said:**
> Hi,

I'm just a couple of weeks born Kubuntu user, and there's one small annoyance I'd love to get some help on.

I have many USB external hard drives, a memory card reader, and a couple of flash drives. Whenever I plug one in, it shows on /dev/sd*, but it's not fixed, sometimes a hard drive will get sdg, sometimes sdi, etc.

How does one assign a fixed location so I can mount those drives more quickly?

I'm on Kubuntu Feisty Fawn x64.

Thanks in advance!

Give the Filesystems on the devices Labels, then they will be all mounted with those names.

Do a search for specific instructions (different for various filesystem types)

---

