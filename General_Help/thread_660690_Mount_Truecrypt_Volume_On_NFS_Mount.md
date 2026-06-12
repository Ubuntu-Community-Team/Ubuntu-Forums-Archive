---
title: "Mount Truecrypt Volume On NFS Mount??"
date: 2008-01-07
forum: General Help
---

### Post by trmentry on 2008-01-07
I'm running Truecrypt on Gutsy (32bit) and its working fine.  However I can't seem to mount a truecrypt volume (file) that is on a NFS mount point.  

The volume is on my server and I have an NFS mount on my laptop to that server.  Truecrypt doesn't seem to like doing that.

If I copy the file locally it works fine.

Is there a way to mount a truecrypt volume from a remote server?



I tested this in Windows, and Truecrypt on windows can mount the volume fine from a Samba share.

Thanks

---

### Post by trmentry on 2008-02-03
Anyone?

I would post to Truecrypt forums, but they appear to be down. :(

---

### Post by Craigus on 2008-02-03
> If I copy the file locally it works fine.

Since you can mount and copy the file, I assume you must have nfs-common installed.

As a test, can truecrpyt create and use a new container on the nfs server ?

---

### Post by trmentry on 2008-02-03
```

trmentry@laptop:~$ df -h
<snip>
server:/home/trmentry      250G  215G   36G  86% /home/trmentry/mnt/server

```

```

trmentry@laptop~$ truecrypt -c mnt/server/tmp/test.tc

Volume type:
 1) Normal
 2) Hidden
Select [1]: 1

Filesystem:
 1) FAT
 2) None
Select [1]: 1

Enter volume size (bytes - size/sizeK/sizeM/sizeG): 5M

Hash algorithm:
 1) RIPEMD-160
 2) SHA-1
 3) Whirlpool
Select [1]: 1

Encryption algorithm:
 1) AES
 2) Blowfish
 3) CAST5
 4) Serpent
 5) Triple DES
 6) Twofish
 7) AES-Twofish
 8) AES-Twofish-Serpent
 9) Serpent-AES
10) Serpent-Twofish-AES
11) Twofish-Serpent
Select [1]: 8

Enter password for new volume 'mnt/server/tmp/test.tc':
Re-enter password:

Enter keyfile path [none]:

TrueCrypt will now collect random data.

To enable mouse movements to be used as a source of random data,
please do one of the following:
- Run TrueCrypt under administrator (root) account.
- Add read permission for your user to device /dev/input/mice.

Please type at least 320 randomly chosen characters and then press Enter:
<SNIP>

Done: 5.00 MB  Speed: 3.30 MB/s  Left: 0:00:00
Volume created.

```

```

trmentry@laptop:~$ truecrypt -u mnt/server/tmp/test.tc mnt/tc
Enter trmentry's or root's system password:
Cannot open volume: Permission denied

```

```

trmentry@laptop:~$ cp mnt/hoth/tmp/test.tc .

trmentry@laptop:~$ truecrypt -u test.tc mnt/tc
Enter password for '/home/trmentry/test.tc':


/dev/mapper/truecrypt0
                      5.0M     0  5.0M   0% /home/trmentry/mnt/tc


```



I also tried mounting the the truecrypt volume locally on the server in my home dir.  It mounts fine.  I then go to browse that dir its mounted in  (~/mnt/tc) via the NFS mount from my laptop (~/mnt/server/mnt/tc)  and get nothing in the list (both cli and nautilus).  However if I browse via Samba to my ~ on the server, I can see the files in the truecrypt volume.  

Server is running Ubuntu 7.10 Server 64bit

Any ideas?

Thanks for the reply.

---

