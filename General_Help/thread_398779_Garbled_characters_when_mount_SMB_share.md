---
title: "Garbled characters when mount SMB share ?"
date: 2007-04-01
forum: General Help
---

### Post by Deadl0ck on 2007-04-01
Hi all,
I've bought a new network hard drive that runs samba.
I can see the shared directories with no problem in Windows.

I can also see them fine with Konqureor from within Ubuntu (using smb://)

The problem is when I try and mount it from the command line. I mount it as follows:

sudo mount -t smbfs //192.168.1.118/public /mnt/test1

That works fine, then if I go to the directory and do a listing I get:

```
cd /mnt/test1
martin@martin-linux:/mnt/test1$ ls -l
total 7562559488
?--------- ? ?    ?                     ?                ?
?--------- ? ?    ?                     ?                ?
-rwxr-xr-x 1 root root 127490112180000000 1940-10-24 03:26 ???
-rwxr-xr-x 1 root root 127490112180000000 1940-10-24 03:26  s??
-rwxr-xr-x 1 root root 128198927640000000 1940-10-24 03:26 ?^?>t??
-rwxr-xr-x 1 root root 128198129820000000 1940-10-24 03:26 v??>t??

```

I have tried differnt character sets, but to no avail....

I have also tried mounting this as cifs:

sudo mount -t cifs //192.168.1.118/public /mnt/test1/

But I get:
mount error 20 = Not a directory
Refer to the mount.cifs( 8 ) manual page (e.g.man mount.cifs)


Anybody got any suggestions ?

---

