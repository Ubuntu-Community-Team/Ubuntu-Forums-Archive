---
title: "Can't uncompress anything"
date: 2008-02-09
forum: General Help
---

### Post by Vadi on 2008-02-09
For some reason, all programs that do the archive decompression in the terminal fail the same way:

"vadi@ubuntu:~/Desktop$ sh NVIDIA-Linux-x86_64-96.43.05-pkg2.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 96.43.05......................................................................................................................................Extraction failed.

Signal caught, cleaning up
vadi@ubuntu:~/Desktop$ "

"vadi@ubuntu:~$ ./vendetta-linux-amd64-installer.sh
Verifying archive integrity... All good.
Uncompressing Vendetta Online for Linux AMD64......................................................................................................................................................................................................................Extraction failed.
Signal caught, cleaning up
vadi@ubuntu:~$ "


What's wrong? :(


Edit: Oh, and for reason, it says /tmp is full when I try and download files. Even though there's practically nothing there. But that might provide a hint..


vadi@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              5767328   5588536         0 100% /
varrun                 1031248        96   1031152   1% /var/run
varlock                1031248         0   1031248   0% /var/lock
udev                   1031248        76   1031172   1% /dev
devshm                 1031248         0   1031248   0% /dev/shm
lrm                    1031248     13320   1017928   2% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3             48045052   2800352  42804096   7% /home
overflow                  1024       612       412  60% /tmp

---

### Post by dcstar on 2008-02-09
> **Vadi said:**
> For some reason, all programs that do the archive decompression in the terminal fail the same way:
.......
Edit: Oh, and for reason, it says /tmp is full when I try and download files. Even though there's practically nothing there. But that might provide a hint..


vadi@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              5767328   5588536         0 100% /
varrun                 1031248        96   1031152   1% /var/run
varlock                1031248         0   1031248   0% /var/lock
udev                   1031248        76   1031172   1% /dev
devshm                 1031248         0   1031248   0% /dev/shm
lrm                    1031248     13320   1017928   2% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3             48045052   2800352  42804096   7% /home
overflow                  **1024       612       412  60% /tmp**

You mount /tmp on a **tiny** partition, and then wonder why file extraction (which uses /tmp) fails?

---

### Post by Vadi on 2008-02-09
I didn't mount it... but thanks for the kind reply. I'm a human here.

---

