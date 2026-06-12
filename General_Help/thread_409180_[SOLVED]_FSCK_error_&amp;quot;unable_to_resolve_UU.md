---
title: "[SOLVED] FSCK error &amp;quot;unable to resolve UUID...&amp;quot;"
date: 2007-04-14
forum: General Help
---

### Post by guguma on 2007-04-14
Hello and good days,

I am using Ubuntu Edgy. The problem is while ubuntu is booting I get an error. It says fsck cannot resolve UUID... and opens me a root command interface. When I say exit Ubuntu boots fine but one of my partitions is not mounted.

I have 2 NTFS partitions, 3 ext3 partitions and one swap. The ext3 and swap partitions are on an extended partition. One ext3 partition is ubuntu root. The others are empty for now.

What I have tried:

1. I used gparted to reformat the unmounted partition as ext3.

2. I opened /etc/fstab and edited it with default options to mount this partition.

The thing is when I create a directory /media/sda8 and use 

```
sudo mount -t /dev/sda8 /media/sda8
``` 

it mounts just fine.

So what is the problem. Thanks in advance.

And another thing (how can i read what device is given which UUID?)

[COLOR="Red"] By the way this is my /etc/fstab[/COLOR]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=b1ed76f2-8926-42fb-b824-76408a64d093 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=1265156715C028D1 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=2E84C22440506475 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=2960bf9e-9780-4637-9f2a-d56f897d6d1e /media/sda5     ext3    defaults        0       2
# /dev/sda7
UUID=7ea2bc0d-d0d1-4012-b66c-cc4ecb1fa489 none            swap    sw            0       0
# /dev/sda8
UUID=00bdfc33-4f6c-4486-b648-db207e7dc535 /media/sda8     ext3    defaults      0       2
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by rai4shu2 on 2007-04-14
What do you get for this:

ls -o /dev/disk/by-uuid/

---

### Post by guguma on 2007-04-14
I get this 

total 0
lrwxrwxrwx 1 root 10 2007-04-14 16:03 1265156715C028D1 -> ../../sda1
lrwxrwxrwx 1 root 10 2007-04-14 16:03 2960bf9e-9780-4637-9f2a-d56f897d6d1e -> ../../sda5
lrwxrwxrwx 1 root 10 2007-04-14 16:03 2E84C22440506475 -> ../../sda2
lrwxrwxrwx 1 root 10 2007-04-14 16:03 77bbda20-d66d-4d79-81fd-e995c4765c7d -> ../../sda8
lrwxrwxrwx 1 root 10 2007-04-14 16:03 b1ed76f2-8926-42fb-b824-76408a64d093 -> ../../sda6
lrwxrwxrwx 1 root 10 2007-04-14 16:39 B423-1C77 -> ../../sdb1
lrwxrwxrwx 1 root 10 2007-04-14 16:03 b5297ea4-8d81-432d-86be-23eddb8ca1a2 -> ../../sda7

Hmm... somethings are pretty messed up right?

sda7 and sda8's UUID's does not fit with my sda7 and sda8 UUID's at /etc/fstab

so how will I fix everything? will overwriting these UUID's to /etc/fstab be enough?

Thanks

---

### Post by rai4shu2 on 2007-04-14
Change /etc/fstab, then:

sudo mount -a

At that point you should be good to go.

---

