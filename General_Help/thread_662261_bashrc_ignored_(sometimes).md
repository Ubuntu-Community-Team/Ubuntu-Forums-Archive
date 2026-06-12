---
title: "bashrc ignored (sometimes)"
date: 2008-01-08
forum: General Help
---

### Post by nnikcm on 2008-01-08
I have a .bashrc file and it works great when I start a command prompt.  However, if I source it (source ~/.bashrc) from the prompt, everything reverts to (what seems to be) the bash.bashrc defaults.  I am not getting any error messages, and cannot use the stuff (custom prompt/aliases) in my .bashrc unless I kill the prompt and open a new one.

I am using Gutsy.

Any suggestions?
Thanks.

---

### Post by nnikcm on 2008-01-08
Found the problem, just in case anyone else has trouble:

[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/160405]("https://bugs.launchpad.net/ubuntu/+source/bash/+bug/160405")

---

