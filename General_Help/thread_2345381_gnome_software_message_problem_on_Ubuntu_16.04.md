---
title: "gnome software message problem on Ubuntu 16.04"
date: 2016-12-03
forum: General Help
---

### Post by John_Carver on 2016-12-03
The following message appears after the boot and upon reloading synaptic
[B]W: [http://archive.canonical.com/ubuntu/dists/precise/Release.gpg:](http://archive.canonical.com/ubuntu/dists/precise/Release.gpg:) Signature by 
key 630239CC130E1A7FD81A27B140976EAF437D05B5 uses weak digest algorithm (SHA1)[/B]

This happens on both 32bit and 64 bit versions

Thanks for reading

---

### Post by cariboo on 2016-12-03
Depending on what point release you are using, Precise may have come to it's EOL. Ubuntu moved to sha2 during the YAkkety cycle, so you will get that error message if trying to use older repositories.

---

