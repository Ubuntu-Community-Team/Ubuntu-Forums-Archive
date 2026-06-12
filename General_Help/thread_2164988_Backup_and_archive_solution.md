---
title: "Backup and archive solution"
date: 2013-08-02
forum: General Help
---

### Post by alagalah on 2013-08-02
Hi there,

I've read some great posts on Rsync as a viable backup option, but what about archive and retrieval?

Ideally I'd like to move a file off to NFS after I haven't accessed it in a while from my /home dir but still keep a link to it, so I can see it. Stretch would be to pull the file back and replace the link after accessing it. 

Anything off the shelf spring to mind?

---

### Post by TheFu on 2013-08-02
I don't know of anything non-commercial and the commercial solutions come with $200K+ storage systems.
Hierarchical Storage Management, HSM, is the normal term.

Standard rsync is not a viable backup solution, but there are many tools build with librsync that are.  rbackup, rdiff-backup, dejadup, duplicity, duplicati, Back-In-Time plus many others all work fine for backups. I've seen differential backup rsync scripts that use hardlinks ... that's what Back-in-Time and rbackup do too.

As to archival, I've never considered the method that you outline, but it is interesting. I might try to script it - not for anything in HOME, but for very large media files stored elsewhere. Clearly softlinks would be required since the files would be on different partitions/disks. I need to think about this for a little bit - hummmmm.  This would mainly be for XBMC media files.

Currently, I have an offline archival system that uses 'ls -lR' text files and numbered media. A grep for the file or name or other stored metadata determines which offline media (optical or HDD) the file is on by the media number, then I manually load it for access.  For optical media, I add 10% par2 files to help correct any bit rot that happens.  After about 5 yrs, a few disks started showing small failures. These were recovered thanks to par2 recovery processing.   More and more, optical disks are a hassle and having this media stored on 3TB HDDs (always 2) would be much more convenient and cheaper.

Archives do not prevent the requirement to have backups. Unless I have 2-4 copies of a file, I don't think I have any.

BTW, I use rdiff-backup for backups across my companies. It has been working well and verified the last 2-4 yrs here. I've had to restore a few times - never had any issues. Full or partial restores. Once in a while a backup will fail, but the next backup sees that failure, rolls it back and works.  Prior to 10.04, running a mix of 10.04 and 8.04 servers, the rdiff-backup versions where not compatible. Since 10.04, I haven't seen any compatibility issues at all.

---

### Post by TheFu on 2013-08-02
Found a few related links. Haven't read them all yet:
* OHSM - [http://sourceforge.net/projects/ohsm/](http://sourceforge.net/projects/ohsm/)
* [http://www.ogris.de/howtos/linux-elcheapo-hsm.html](http://www.ogris.de/howtos/linux-elcheapo-hsm.html)
* [https://lwn.net/Articles/375828/](https://lwn.net/Articles/375828/)

Very interesting stuff.

---

