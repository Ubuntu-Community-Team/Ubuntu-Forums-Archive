---
title: "Third -party sources file"
date: 2024-09-27
forum: General Help
---

### Post by cairnsww2 on 2024-09-27
I have made a successful upgrade to 24.04. However, my Third party sources file at /etc/apt/sources.list.d/Third-party sourced is corrupt and stood like this:

Types: deb
URIs: cdrom:[Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1)]/
Suites: jammy
Components: main restricted: 

This is obviously nonsense - I do not have a cdrom and am (presumably) looking to use 'noble' rather than jammy. I have managed a quick work atound by inserting 'Enabled: no' as the first line.

But what should the file look like?

---

### Post by davetheoldcoder on 2024-09-27
The URIs line should contain a valid URL or URL's.

Example:
```
URIs: [http://example.com](http://example.com)
```

---

### Post by cairnsww2 on 2024-09-30
Thanks - Could sopmeone give me the exact contents that I need on my sources file so that I can rebuild it. I know it should have a valid URL - but what URL do I need?

---

### Post by tea for one on 2024-09-30
Ubuntu 24.04: From /etc/apt/sources.list.d - file name is ubuntu.sources
```
Types: deb
URIs: http://gb.archive.ubuntu.com/ubuntu/
Suites: noble noble-updates noble-backports
Components: restricted universe multiverse main
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg

Types: deb
URIs: http://security.ubuntu.com/ubuntu/
Suites: noble-security
Components: multiverse main universe restricted
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
```
You may wish to change gb to your usual mirror

---

### Post by cairnsww2 on 2024-09-30
Thanks. I think that is just what I needed!

---

