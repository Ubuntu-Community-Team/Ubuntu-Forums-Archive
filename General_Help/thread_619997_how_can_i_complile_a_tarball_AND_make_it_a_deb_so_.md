---
title: "how can i complile a tarball AND make it a deb so it shows up in synaptic?"
date: 2007-11-22
forum: General Help
---

### Post by erlinux on 2007-11-22
how can i complile a tarball AND make it a deb so it shows up in synaptic? got a link?
i never needed to do this, but since ive switched to 64bit i need this
also what is SVN and how do i use it?

---

### Post by pedrogl on 2007-11-22
You can use checkinstall.
For a common tarball, you do the following sequence:
```
cd app_folder
./configure --prefix=/usr
make
sudo checkinstall
``` 
Last line (instead of the usual make install) create and install deb files.
But be warned that debs generated with this method won't contain info about package dependencies and stuff like that

---

