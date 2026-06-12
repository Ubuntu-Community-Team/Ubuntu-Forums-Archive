---
title: "apt update fails in 18.04"
date: 2018-05-10
forum: General Help
---

### Post by m-dw on 2018-05-10
I have a new installation of Ubuntu server 18.04 LTS (replacing 16.04 LTS, following a failed hard disk. Recently "sudo apt update" has failed with the following error:

```

david@srvbuntu:~$ sudo apt update
Get:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [69.9 kB]
Get:2 http://archive.ubuntu.com/ubuntu bionic InRelease [242 kB]
Get:3 http://archive.ubuntu.com/ubuntu bionic-updates InRelease [65.4 kB]
0% [1 InRelease gpgv 69.9 kB] [3 InRelease 0 B/65.4 kB 0%]terminate called after throwing an instance of 'std::runtime_error'
  what():  random_device::__x86_rdrand(void)
Aborted

```

Really I'm clueless to troubleshoot this. I've done a (quick) search on the internet but got nowhere (nothing relating to apt). Is it something to do with /dev/random perhaps? Can someone offer advice?

---

### Post by m-dw on 2018-05-10
OK, ignore that. Fixed by disconnecting external drive (which has a bitlocker encrypted partition) and rebooting.

---

