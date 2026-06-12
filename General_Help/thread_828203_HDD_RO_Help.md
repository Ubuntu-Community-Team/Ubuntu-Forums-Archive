---
title: "HDD RO Help"
date: 2008-06-13
forum: General Help
---

### Post by Reonarudo on 2008-06-13
Hello,
I have an extern HDD that is constantly in read only mode, I have formated into fat16, fat32, ext2 and ext3 ans still doesn't let me save anything on it, so I tried :~$ sudo fsck -a /dev/sdb and it presents me the folowing message:

fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb
/dev/sdb: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

So as sugested I did ~$ sudo e2fsck -b 8193 /dev/sdb and this time it shows me this:

e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/sdb
Filesystem mounted or opened exclusively by another program?

and as far as I know nothing is using the hdd and it is unmounted.
So please help me if you can. :(

---

### Post by logos34 on 2008-06-13
you need to specify a partition, like sdb[COLOR="Red"]1[/COLOR], sdb[COLOR="Red"]2[/COLOR], etc. whatever it is

format it ext3, then chown it.  See if that works

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(--> bottom)

---

### Post by Reonarudo on 2008-06-13
Thank you, but I specified de partition as being sdb1 and the problem presists :/

---

