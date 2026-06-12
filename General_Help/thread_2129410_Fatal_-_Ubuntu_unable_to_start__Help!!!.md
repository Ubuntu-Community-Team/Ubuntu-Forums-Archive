---
title: "Fatal - Ubuntu unable to start  Help!!!"
date: 2013-03-26
forum: General Help
---

### Post by satimis on 2013-03-26
Hi all,

Host - Ubuntu 12.04 desktop 64bit
Oracle Virtualbox

Ubuntu fails to start with following warning;```

FATAL Could not load /lib/modules 3.5.0-26-generic/module dep no such file or directory

```
Please advise how to fix this problem.  TIA

IIRC 3 hours ago I ran apt-get update/upgrade before closing down the PC.  

I can start recover mode but the wireless keyboard can't work.  I have another HD on this PC also running Ubuntu12.04 which is still working.  I won't run update/upgrade disregarding the notice of Update Manager.

B.R.
satimis

---

### Post by dino99 on 2013-03-26
i suppose the upgrade was not ended when you have shut it down. You might recover it by booting into recovering mode, then activate the network, and finally repair the broken packages. But you maybe have an other kernel installed to boot with on that hdd.

---

### Post by satimis on 2013-03-26
> **dino99 said:**
> i suppose the upgrade was not ended when you have shut it down. 

Hi,

IIRC I ran apt-get update/upgrade on both host-ubuntu12.04 and VM-ubuntu12.04(guest) simultaneously.  Both processes have been finished.  I have been working on WordPress running on VM(guest) for at least 3 hrs. before closing down the PC.

> 
You might recover it by booting into recovering mode, then activate the network, and finally repair the broken packages. 
Yes I can boot recover mode but the wireless keyboard is NOT work.  How can I activated the network?  I can't keyin?  Thanks

> 
But you maybe have an other kernel installed to boot with on that hdd.
I'll check later.  I'm now replying on another HD, on the same PC.  If I can boot the old kernel please advise how to fix the problem.  Re-run apt-get update/upgrade?  Thanks


Edit-1:
Now I boot the old kernel (GNU/Linux 3.5.0-25-generic x86_64) to reply you.

Edit-2:
Just boot the VM which has been update/upgrade at the same time.  It is now working seemingly without problem.

B.R.
satimis

---

