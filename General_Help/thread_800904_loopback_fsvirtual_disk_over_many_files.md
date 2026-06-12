---
title: "loopback fs/virtual disk over many files"
date: 2008-05-20
forum: General Help
---

### Post by sleemanj on 2008-05-20
Here's the situation.  A home NAS which can only do FAT32 as it's filesystem, serving over samba.  

This of course has with it the 4gb samba limit.  I want to use this as a backup device (somewhat remote) but it may need to backup files >4gb, and I also want to use a better fs in general so permissions and such can be preserved.

Anybody know a way I could perhaps create a loopback e2fs or similar split over several (less than 4gb)  files?  

I think I could bodge togethor a system using a virtual disk created in vmware and the vmware-mount tool, but, it would be pretty kludgy if I ever needed to restore the backup from scratch (I'd need vmware installed first).

---

### Post by sdennie on 2008-05-20
I don't know of a way to get around a 4GB file size limit however, there is a split command on linux.  I would check "man split" in a terminal to find out more about it.  You may also want to create a huge tarball and split it.  In which case, I would look into the tar command (man tar will work but, you may want to find a tutorial on it).

---

