---
title: "help root folder messed up"
date: 2016-03-19
forum: General Help
---

### Post by Branden_Tisdell on 2016-03-19
Hi I am running Ubuntu 14.04 with an i7 and nvidia 650M....I cant update because there inst enough room in the root folder, I have 40GB of space allocated to root and its ridiculous that all that space is being used and bleach-bit or terminal commands don’t help I cant find whats taking all the space can anyone help??

---

### Post by howefield on 2016-03-19
All that 40gb of space isn't used (or at least, it is highly unlikely), but the space allocated to /boot which is where the kernels (old and new) reside sounds like it is.

The easiest option would be to run the command

```
sudo apt-get autoremove
```

which should try to remove all bar the latest 2 kernels. If it doesn't work then the old kernels will have to be manually removed, let us know how autoremove gets on.

---

