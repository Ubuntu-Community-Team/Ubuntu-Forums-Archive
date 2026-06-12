---
title: "meta-package for libxcb?"
date: 2021-04-08
forum: General Help
---

### Post by tkacvins on 2021-04-08
Is there a meta-package for all libxcb related packages?  I face an issue where I need a lot of libxcb*.so.*
files installed, and rather than hunt done each one, I'd prefer to install them all in one fell swoop.

Thanks,

Tom

---

### Post by tkacvins on 2021-04-08
Answering my own question:

apt-get update -y
apt-get install -t libxcb*

That installed everything I needed.

---

