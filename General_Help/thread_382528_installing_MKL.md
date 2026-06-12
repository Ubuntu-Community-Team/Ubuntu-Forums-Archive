---
title: "installing MKL"
date: 2007-03-12
forum: General Help
---

### Post by hutxubix on 2007-03-12
Hello,

There are other threads about this topic, but I haven't been able to install MKL on edgy. I had installed it on Ubuntu 6.06, but as it has already been said, things are different in Edgy.

What has been said is to change /bin/sh to /bin/bash in the installer scritpts to get the installer to make the .rpm in /tmp/mkl. Then, using alien and dpkg, it can be installed.

However, in my case, I have never got it to have the .rpm in /tmp/. The message I get is:

./.././install/install: line 302: /tmp/install_temp.3f2d4826bb58650b42bd03071f1d5339/install32: no se puede ejecutar el archivo binario (binary archive can not be executed)
Warning: It seems installation failed
Deleting temporary files...


Could anyone help me? I'm getting mad with these¡

Thanks

---

### Post by hutxubix on 2007-03-13
nobody?

---

