---
title: "/dev/sda: Bad magic number in super-block"
date: 2014-09-18
forum: General Help
---

### Post by diyhouse on 2014-09-18
Need some help as feeling vulnerable as no means of restore,.. when creating a new bootable system...

Now my problems started with not being able to successfully restore a dd file save,... and for this I looked for help in the following thread

[http://ubuntuforums.org/showthread.php?t=2241905](http://ubuntuforums.org/showthread.php?t=2241905)

have made some dump saves,...  with the idea of creating some fall back if all goes wrong.

Anyway tried to dump the entire disk,.. by specifying "/dev/sda"  , full command as follows:-

dump -0uz2 -f /mnt/disky/OS-disk/sysimage-sda-18Sept14.dump.z /dev/sda

but this got the following error:-

root@sysresccd /root % dump -0uz2 -f /mnt/disky/OS-disk/sysimage-sda-18Sept14.dump.z /dev/sda
  DUMP: Date of this level 0 dump: Thu Sep 18 10:13:18 2014
  DUMP: Dumping /dev/sda (an unlisted file system) to /mnt/disky/OS-disk/sysimage-sda-18Sept14.dump.z
  /dev/sda: Bad magic number in super-block while opening filesystem
  DUMP: The ENTIRE dump is aborted.



disk is a 128gig SSD, sysrescue CD is 4.1,.. is the formatting screwed up,... would this explain why dd restore failed to restore before.. 

can I fix with a re-install of grub,..  although trying to create NEW bootable disk but still working on how to install grub on to clean partitioned disk (WIP), any pointers here welcome...

Many thanks

---

### Post by diyhouse on 2014-09-20
Further developments here are that I finally managed to created a cloned disk,.. although loading grub did prove to be a challenge.

So with new cloned disk,..  tried to image entire disk with dump,.. and it failed in the same way,.. "bad magic number"

So either dump is not capable of dumping the entire disk or I have other problems,.. is there a SME out there able to enlighten me... as I am still looking for some means of backing up my system.

Kind Regards

---

### Post by diyhouse on 2014-09-20
Unless anyone can tell me otherwise,.. following further research,. I am led to believe that a complete disk backup is not possible with the likes of dump and dd,... 

Each partition must be backed up as an individual save set,.. ( and maybe concatenated into a single save-set ).

So the "bad magic number" is as a consequence of trying to do something that is not actually possible. 

pls correct me if I am mistaken

---

