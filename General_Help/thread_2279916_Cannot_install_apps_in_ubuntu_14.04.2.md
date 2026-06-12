---
title: "Cannot install apps in ubuntu 14.04.2"
date: 2015-05-26
forum: General Help
---

### Post by Lijun on 2015-05-26
Hi everyone,

I am experencing a problem since I tried to install adobe reader. The installation failed, and thereafter whenever I try to install an app it says that some packages will be installed and are not autenticated.

For example, when I tried to install udisk, I get the following 

lijun@lijun-X230:~$ sudo apt-get install udisks
[sudo] password for lijun: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cryptsetup-bin libcryptsetup4 libdevmapper-event1.02.1 liblvm2app2.2
Suggested packages:
  xfsprogs reiserfsprogs mdadm
The following NEW packages will be installed:
  cryptsetup-bin libcryptsetup4 libdevmapper-event1.02.1 liblvm2app2.2 udisks
0 upgraded, 5 newly installed, 0 to remove and 13 not upgraded.
Need to get 583 kB of archives.
After this operation, 2 389 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  libdevmapper-event1.02.1 liblvm2app2.2 libcryptsetup4 cryptsetup-bin udisks
Install these packages without verification? [y/N] n
E: Some packages could not be authenticated


Can anyone help?

Thank you so much.

---

### Post by ajgreeny on 2015-05-26
How did you try to install Adobe reader?  Did you download AdbeRdr9.5.5-1_i386linux_enu.deb and try installing that package or use some other method.

---

### Post by Lijun on 2015-05-29
Thanks. Yes I download AdbeRdr9.5.5-1_i386linux_enu.deb and tried to install but failed.

Wired thing is that after a reboot and changed the server to the Main Server, did a update, then it works again. Failed to install adobe reader but at least I can install apps again.

Thanks again for the help. 


> **ajgreeny said:**
> How did you try to install Adobe reader?  Did you download AdbeRdr9.5.5-1_i386linux_enu.deb and try installing that package or use some other method.

---

### Post by ajgreeny on 2015-05-31
I just tried this myself and got a similar problem with broken packages and no ability to install anything else.
I fixed that after some messing around and did eventually get acroread installed but it would not start, just threw error messages so I gave up as I did not need it anyway.

---

