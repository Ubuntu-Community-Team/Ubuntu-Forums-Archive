---
title: "Cannot install Kernel 4.15.0-24"
date: 2018-07-05
forum: General Help
---

### Post by Hewjr100 on 2018-07-05
A previous installation installed 4.15.0-24 But I had to reinstall in Bios mode so I could install Nvidia proprietary driver.  This install only has 4.15.0-23.  Tried to install 4.15.0-24 and got the following:

```
henry@wyatt:~$ uname -a
Linux wyatt 4.15.0-23-generic #25-Ubuntu SMP Wed May 23 18:02:16 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
henry@wyatt:~$ sudo apt install 4.15.0-24
[sudo] password for henry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-image-unsigned-4.15.0-24-lowlatency' for regex '4.15.0-24'
Note, selecting 'linux-tools-4.15.0-24-generic' for regex '4.15.0-24'
Note, selecting 'linux-headers-4.15.0-24' for regex '4.15.0-24'
Note, selecting 'linux-headers-4.15.0-24-lowlatency' for regex '4.15.0-24'
Note, selecting 'linux-headers-4.15.0-24-generic' for regex '4.15.0-24'
Note, selecting 'linux-cloud-tools-4.15.0-24-lowlatency' for regex '4.15.0-24'
Note, selecting 'linux-modules-extra-4.15.0-24-generic' for regex '4.15.0-24'
Note, selecting 'linux-cloud-tools-4.15.0-24' for regex '4.15.0-24'
Note, selecting 'linux-tools-4.15.0-24' for regex '4.15.0-24'
Note, selecting 'linux-image-unsigned-4.15.0-24-generic' for regex '4.15.0-24'
Note, selecting 'linux-tools-4.15.0-24-lowlatency' for regex '4.15.0-24'
Note, selecting 'linux-modules-4.15.0-24-generic' for regex '4.15.0-24'
Note, selecting 'linux-image-4.15.0-24-lowlatency' for regex '4.15.0-24'
Note, selecting 'linux-modules-4.15.0-24-lowlatency' for regex '4.15.0-24'
Note, selecting 'linux-image-4.15.0-24-generic' for regex '4.15.0-24'
Note, selecting 'linux-cloud-tools-4.15.0-24-generic' for regex '4.15.0-24'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-image-4.15.0-24-generic : Conflicts: linux-image-unsigned-4.15.0-24-generic but 4.15.0-24.26 is to be installed
 linux-image-4.15.0-24-lowlatency : Conflicts: linux-image-unsigned-4.15.0-24-lowlatency but 4.15.0-24.26 is to be installed
 linux-image-unsigned-4.15.0-24-generic : Conflicts: linux-image-4.15.0-24-generic but 4.15.0-24.26 is to be installed
 linux-image-unsigned-4.15.0-24-lowlatency : Conflicts: linux-image-4.15.0-24-lowlatency but 4.15.0-24.26 is to be installed
E: Unable to correct problems, you have held broken packages.
henry@wyatt:~$ 

```

sudo apt install -f did nothing.

Henry

---

### Post by monkeybrain20122 on 2018-07-05
4.15.0-24 is broken, there are many threads on it in the last 36 hrs or so. Stick to 4.15.0-23 and you should be fine.

---

### Post by Hewjr100 on 2018-07-05
Got it, thanks.  I thought it was on my end.

Henry

---

