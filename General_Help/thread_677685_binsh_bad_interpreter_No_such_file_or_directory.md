---
title: "/bin/sh: bad interpreter: No such file or directory"
date: 2008-01-25
forum: General Help
---

### Post by kpm on 2008-01-25
Hi, I was following along with a how to and rather messed up the shell, or bash, or both...
I issued the following command:
ln -sf /bin/bash /bin/sh
The rationale was that this would make an install of ispconfig work, which I realized I didn't want and decided I wanted the original shell so figured I could simply delete the link so issued:
rm /bin/sh
Unfortunately now, when I attempt to issue a command like a2ensite [www.example.com](www.example.com), I get the following error:
-bash: /usr/sbin/a2enmod: /bin/sh: bad interpreter: No such file or directory

Is there an easy repair for this mistake? I tried apt-get install bash, but same problem persists.

Thanks

---

### Post by jeffus_il on 2008-01-25
A non-expert response.
I would have expected that removing the link would solve the problem.
Have you done a reboot?
The repository has a package called "sash" which is a small stand-in for the original "sh" shell. Installing it is quick and I'm sure won't have side effects, want to try it?
No not necessary, I have "sh", tried it at the command prompt, maybe you should reinstall sh, but I don't know which package it's in, will look around.

On my system sh is linked to dash,
```
 lrwxrwxrwx  1 root root       4 2007-11-29 03:24 sh -> dash
```Yours should be bash

so you need to link sh to bash, so redo the link.

---

