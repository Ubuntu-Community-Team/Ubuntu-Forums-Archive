---
title: "/etc/grub.d/20_xen_linux missing even after reinstall"
date: 2013-06-23
forum: General Help
---

### Post by lokex on 2013-06-23
I removed xen-* with apt-get remove --purge xen-* and deleted all the files from /boot and /etc/grub.d that were related to it. For some reason on reinstalling the package xen-system-amd64, the files are not being recreated. How do I force it to do so? I am also unable to find this file in package search for Ubuntu online as well. 

My system:
Linux 3.8.0-19-generic #29-Ubuntu SMP x86_64 GNU/Linux
Ubuntu 13.04 amd64

Thanks

---

### Post by gordintoronto on 2013-06-23
Are you running Ubuntu in a virtual machine? Why do you think this file is useful?

---

