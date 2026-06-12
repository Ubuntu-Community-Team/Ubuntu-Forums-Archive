---
title: "Problems installing OCFS2 on 6.10"
date: 2007-04-13
forum: General Help
---

### Post by mattbennett on 2007-04-13
Hello,

I'm having problems getting OCFS2 running on Edgy. I've installed the tools package (ocfs2-tools), but when I try to load o2cb I get this:

```
dev@vlan:~$ sudo /etc/init.d/o2cb load
Loading module "ocfs2_nodemanager": Unable to load module "ocfs2_nodemanager"
Failed
```

o2cb's status then produces:

```
dev@vlan:~$ sudo /etc/init.d/o2cb status
Module "configfs": Loaded
Filesystem "configfs": Mounted
Module "ocfs2_nodemanager": Not loaded
Module "ocfs2_dlm": Not loaded
Module "ocfs2_dlmfs": Not loaded
Filesystem "ocfs2_dlmfs": Not mounted
```

My kernel is 2.6.17-10-generic. I thought this kernel had all the ocfs2 modules included in it. Am I wrong? 

```
sudo updatedb
sudo locate ocfs2_nodemanager
``` also does not find anything.

I can't find any logs which specify what's going wrong. Can anyone point me in the right direction?

Many thanks,
Matt.

---

### Post by acormack on 2007-04-14
I have never done any clustering, but are you sure you have all the kernel modules loaded that you need for this application?

the **lsmod** command shows you what kernel modules you have loaded 

and the **insmod** command installs additional ones

Were you following some sort of  howto guide to get this application installed?


Alec

---

### Post by mattbennett on 2007-04-14
Hi Alec,

I was just following the manual for ocfs2. Since it's been supported in the vanilla kernel since 2.6.16, it should not need to be installed as a module.

It's worth noting that it works out of the box on Dapper. I wonder if it's been forgotten and left out of the Edgy kernel somehow?

Matt.

---

### Post by Lars Lerager on 2007-06-06
You have probably solved this problem by now.
But as far as I know, the 2.6.16 kernel only had 'experimental' OCFS2 support. This means that support isn't compiled in on stock kernels unless you specifically enable it.
OCFS2 support was taken out of 'experimental' with the 2.6.19 kernel.

---

### Post by mattbennett on 2007-06-07
Lars,

I never did solve the issue with Edgy. You're right that support was marked as 'experimental' from 2.6.16 to 2.6.18, but OCFS2 works out-of-the-box on a vanilla Dapper install - so something must have been broken in the Edgy release (or else Dapper was compiled with the 'experimental' support enabled and Edgy wasn't).

Matt.

---

