---
title: "Nautilus: cannot mount samba share"
date: 2013-03-11
forum: General Help
---

### Post by maxxer on 2013-03-11
Hi.
I've a Samba server on my LAN, and several Ubuntu clients. One of these clients cannot mount the samba share! 
This client is a 12.04 fully updated, it used to work until some updates ago.
When I try to access the "smb://" location in nautilus I get something like this (freely translated from italian):
> Nautilus is unable to handle "smb:" locations

From command line:
```
$ gvfs-mount smb://server/share
Error mounting location: volume doesn't implement mount action
```

smbclient works great. mount works great.

```
$ dpkg -l |grep cifs
ii  cifs-utils                             2:5.1-1ubuntu1                                      Common Internet File System utilities
$ dpkg -l |grep smb
ii  libsmbclient                           2:3.6.3-2ubuntu2.3                                  shared library for communication with SMB/CIFS servers
ii  python-smbc                            1.0.13-0ubuntu1                                     Python bindings for Samba clients (libsmbclient)
ii  smbclient                              2:3.6.3-2ubuntu2.3                                  command-line SMB/CIFS clients for Unix
ii  smbfs                                  2:5.1-1ubuntu1                                      Common Internet File System utilities - compatibility package
# dpkg -l |grep gvfs
ii  gvfs                                   1.12.1-0ubuntu1.1                                   userspace virtual filesystem - GIO module
ii  gvfs-backends                          1.12.1-0ubuntu1.1                                   userspace virtual filesystem - backends
ii  gvfs-bin                               1.12.1-0ubuntu1.1                                   userspace virtual filesystem - binaries
ii  gvfs-common                            1.12.1-0ubuntu1.1                                   userspace virtual filesystem - common data files
ii  gvfs-daemons                           1.12.1-0ubuntu1.1                                   userspace virtual filesystem - servers
ii  gvfs-fuse                              1.12.1-0ubuntu1.1                                   userspace virtual filesystem - fuse server
ii  gvfs-libs                              1.12.1-0ubuntu1.1                                   userspace virtual filesystem - private libraries
root@pietro-aio:~# uname -a
Linux pietro-aio 3.2.0-38-generic-pae #61-Ubuntu SMP Tue Feb 19 12:39:51 UTC 2013 i686 i686 i386 GNU/Linux
```

I even tried [this]("http://askubuntu.com/questions/161187/why-is-my-machine-unable-to-mount-my-smb-drives-cifs-vfs-error-connecting-to") but doesn't seem to work.

What's wrong?
Thanks

---

### Post by Morbius1 on 2013-03-11
> 
root@pietro-aio:~# uname -a
Because you are logged in as root. Log in as a non-root user and try it again.

---

### Post by maxxer on 2013-03-11
thanks but from the commands you can see above, gvfs-mount was issued as user, not as root. only package and diagnostic commands were ran as root user

---

