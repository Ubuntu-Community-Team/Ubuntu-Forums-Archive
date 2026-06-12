---
title: "permissions on copied files (SD card)"
date: 2007-08-03
forum: General Help
---

### Post by skathrein on 2007-08-03
Any advice on the following:
If I copy files from my camera (SD card) to my hard drive, it will allow me full access to those files but not other users.  Ideally, I would like all users to have all rights (rwx) to the files.  I know that I can run chmod on the files once they are on my hard drive to allow everyone access to them, however, I would like something more automatic.  I can also set the acl on the folder where they are copied to, however, this only governs new files created in that directory and therefore doesn't work.  In other words, ACL will not alter the permissions of files already created somewhere else and then copied into the subject directory.  Another option might be to do something like adding acl to the options when mounting the SD card, however, it is auto-mounted and therefore is not currently a fstab entry.  Any suggestions would be appreciated.  Thanks.

---

### Post by kidders on 2007-08-04
Hi there,

Most Linux users don't bother with ACL-based access control. You *could* just set the SGID bit on your destination directory (assuming you and all the people you want to allow access to your files are already members of the group that owns it). In permissions terms, there is no difference between a copied file and a newly created one, since (if you think about it) a copied file *is* a newly created one ... so that really ought to work for you. :-)

You might also be interested in taking a look at cp's man page for details on how it handles filesystem permissions & ownership. By default (as you know) it overwrites them with permissions extracted from your working environment (eg your primary group membership & umask), unless told to do otherwise.

---

### Post by bsmith1051 on 2008-03-09
Could someone please elaborate on how the SGID bit setting works?  I thought I'd done this (or something similar) but all my copied photos still end-up with Group=No Access permissions.  My wife and I have separate logins and use a 'shared' Photos folder, and so this problem creates a lot of extra work as neither of us can access the photos imported by the other. . .

P.S.  "Arise old thread!!!"

---

