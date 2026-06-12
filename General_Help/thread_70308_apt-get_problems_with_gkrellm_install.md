---
title: "apt-get problems with gkrellm install"
date: 2005-09-29
forum: General Help
---

### Post by benkomalo on 2005-09-29
Hello folks,

This is sort of an odd problem. I used to have gkrellm (I'm not sure if it's because it came with Ubuntu, which I don't think it did, or if I did and apt-get for it before).  But everytime I ran apt-get it gave me some dependency error about gkrellm. Being the noob I am and not knowing exactly how to fix the error message I randomly tried things and ran apt-get -f install, which seemed to have removed gkrellm.  Which is unfortunate since I want gkrellm.

Now when I try to install it I get the following error:

```
bkomalo@lnx-bkomalo:~$ sudo apt-get install gkrellm-common
Reading package lists... Done
Building dependency tree... Done
Package gkrellm-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gkrellm-common has no installation candidate
```

I've tried installing from source as well but the source doesn't seem to build nicely on my machine.  

I'm not really familliar with apt so I'm not sure what this sort of error message means. If anyone could provide guidance, I'd be more than appreciative.

Ben

---

