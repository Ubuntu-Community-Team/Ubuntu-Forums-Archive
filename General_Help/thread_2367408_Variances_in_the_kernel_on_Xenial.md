---
title: "Variances in the kernel on Xenial"
date: 2017-07-29
forum: General Help
---

### Post by DigiAngel on 2017-07-29
So I have 4 Ubuntu Xenial boxes, one is a VM.  My process after install is to do a dist-upgrade, and then enable the LTS hardware stack by doing the below per [https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"):

```

sudo apt-get install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04 

```

So...why do these machines have different kernels?  The below results are all after doing a fresh apt-get update and apt-get dist-upgrade.  I've not done any manual kernel additions or removals of kernels:
```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
virtual-machine:~$ uname -a
Linux virtual-machine 4.8.0-58-generic #63~16.04.1-Ubuntu SMP Mon Jun 26 18:08:51 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
Video:~$] uname -a
Linux Video 4.8.0-41-generic #44~16.04.1-Ubuntu SMP Fri Mar 3 17:11:16 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
analysis:~$ uname -a
Linux analysis 4.8.0-42-generic #45~16.04.1-Ubuntu SMP Thu Mar 9 14:10:58 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

LSB Version:	core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
gamebox:~$] uname -a
Linux gamebox 4.10.0-28-generic #32~16.04.2-Ubuntu SMP Thu Jul 20 10:19:48 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

Thank you.

---

### Post by deadflowr on 2017-07-29
*Thread moved to **General Help***

---

### Post by rsteinmetz70112 on 2017-07-30
I've been trying to figure out more or less the same thing. See my thread[ here]("https://ubuntuforums.org/showthread.php?t=2367403").

---

### Post by DigiAngel on 2017-08-01
Thanks that's helpful.

---

