---
title: "software updater problem - not enough disk space"
date: 2014-10-05
forum: General Help
---

### Post by linux.girl on 2014-10-05
Hi, I am trying to run the updates suggested by the software updater (on ubuntu latest version) and for some reason I get the attached message. How do I fix it? I have more than 300GB of free disk space, so I dont understand :-([ATTACH=CONFIG]256960[/ATTACH]


Thanks in advance!

---

### Post by Impavidus on 2014-10-05
There is enough space on your root partition, but it's your /boot partition that's full. Most people don't have one. Have you installed using LVM or full disk encryption? That may lead to this problem.

Try uninstalling some old kernels:```
sudo apt-get --purge autoremove
```If that doesn't help we'll have to do it manually. In that case provide the output of these two commands:```
uname -r
dpkg --list linux-image*
```(Maximise your terminal window first. The output may be a little wide.)

---

### Post by linux.girl on 2014-10-09
Hi Impavidus - I did the first suggestion - it seemed to have cleaned quite a lot, but when I tried to install the updates, the popup message appeared again.

So here are the output of the commands you gave me:

linux:~$ uname -r
3.13.0-36-generic

linux:~$ dpkg --list linux-image*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-image                                   <none>                      <none>                      (no description available)
un  linux-image-3.0                               <none>                      <none>                      (no description available)
rc  linux-image-3.11.0-19-generic                 3.11.0-19.33                amd64                       Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-20-generic                 3.11.0-20.35                amd64                       Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-22-generic                 3.11.0-22.38                amd64                       Linux kernel image for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-3.11.0-23-generic                 3.11.0-23.40                amd64                       Linux kernel image for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-30-generic                 3.13.0-30.55                amd64                       Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                 3.13.0-32.57                amd64                       Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                 3.13.0-34.60                amd64                       Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                 3.13.0-35.62                amd64                       Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                 3.13.0-36.63                amd64                       Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-19-generic           3.11.0-19.33                amd64                       Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-20-generic           3.11.0-20.35                amd64                       Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-22-generic           3.11.0-22.38                amd64                       Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-extra-3.11.0-23-generic           3.11.0-23.40                amd64                       Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-30-generic           3.13.0-30.55                amd64                       Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic           3.13.0-32.57                amd64                       Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic           3.13.0-34.60                amd64                       Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic           3.13.0-35.62                amd64                       Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic           3.13.0-36.63                amd64                       Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                           3.13.0.36.43                amd64                       Generic Linux kernel image

Thanks again!

---

### Post by ibjsb4 on 2014-10-09
```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Advanced_users](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Advanced_users)
This will remove all old kernels, then ..
```
sudo apt-get update && sudo apt-get dist-upgrade && sudo reboot
```
This will install the latest kernel (3.13.0-37) and leave the current kernel (3.13.0-36) for backup.

---

### Post by linux.girl on 2014-10-09
Thanks lbjsb4 - that solved the problem!!!

---

