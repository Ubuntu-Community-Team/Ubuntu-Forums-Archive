---
title: "ext3 partitioning using more space than fat32?"
date: 2008-05-14
forum: General Help
---

### Post by uberlinux on 2008-05-14
I have two identical external 500GB HDDs, one is FAT32, and one is ext3.  The FAT32 one has 466GB usable after partitioning, and the ext3 one only has 435GB usable.  Could it really be that FAT32 makes better use of disk?

---

### Post by ibuclaw on 2008-05-14
It's not that.
Infact it's quite the opposite.

The added "space-loss" is for the Ext3 filesystem to handle all caching of file movements. Being a Journalised Filesystem (unlike FAT32) that does not defrag easily (Again, unlike FAT32). It requires a little more space to keep this up and to handle the internal processes of file movements, something that the filesystem does quite alot of in one session.
But this is nothing that you never should really be concerned about, let alone notice.

Although it may seem like a pointless waste if you have, say 2 files on the disk.
But think about 400GBs of files on that disk and it makes some more sense. It requires that extra space to control movement of files and keep down the level of fragmentation.

Windows users will agree, A completely full FAT32 filesystem is an undefragable bomb in a nutshell.

But what am I saying? 500GB is a hell of a lot hard-drive, you won't be using that space up in a hurry (My Ubuntu size is currently struggling to stay at up at a size 20GB... :D )

Regards
Iain

---

### Post by Oldsoldier2003 on 2008-05-14
if you are concerned about the overhead (7.5% on ext3 ) you could always use jfs.

---

### Post by uberlinux on 2008-05-14
> **tinivole said:**
> It's not that.


But what am I saying? 500GB is a hell of a lot hard-drive, you won't be using that space up in a hurry (My Ubuntu size is currently struggling to stay at up at a size 20GB... :D )


1.5TB of brushed aluminum goodness, and that just the EXTERNAL storage!!
[IMG]http://downlink.homeunix.org/techpics/HDDstack.jpg[/IMG]

---

### Post by redoscar3 on 2008-05-14
> 1.5TB of brushed aluminum goodness, and that just the EXTERNAL storage!!

Sweet!

---

### Post by psusi on 2008-05-15
> **tinivole said:**
> It's not that.
Infact it's quite the opposite.

The added "space-loss" is for the Ext3 filesystem to handle all caching of file movements. Being a Journalised Filesystem (unlike FAT32) that does not defrag easily (Again, unlike FAT32). It requires a little more space to keep this up and to handle the internal processes of file movements, something that the filesystem does quite alot of in one session.
But this is nothing that you never should really be concerned about, let alone notice.

I think you meant does not FRAGMENT easily.  Defrag would be the process of removing excess fragments from the filesystem.  Also this business of file "movements" is total made up voodoo.  Once written, files don't "move".  The explanation for the missing space is really quite simple:

By default, ext3 reserves 5% of the total disk space for emergency use by root only.  You can adjust this with the tune2fs command.

> **tinivole said:**
> 
Although it may seem like a pointless waste if you have, say 2 files on the disk.
But think about 400GBs of files on that disk and it makes some more sense. It requires that extra space to control movement of files and keep down the level of fragmentation.

Again, the files never move once they are written ( unless you run an offline e2defrag, but nobody ever does that ).  Ext3 minimizes fragmentation by simply placing the files in wide open spaces in the first place, instead of the very first available free space like windows does.

> **tinivole said:**
> 
Windows users will agree, A completely full FAT32 filesystem is an undefragable bomb in a nutshell.

All filesystems will become rather fragmented when very full.  Windows just has a nasty tendency to cause very heavy fragmentation all the time due to its poor allocation policies.

---

