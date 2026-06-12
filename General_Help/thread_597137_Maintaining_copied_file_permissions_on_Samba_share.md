---
title: "Maintaining copied file permissions on Samba share"
date: 2007-10-30
forum: General Help
---

### Post by Naatan on 2007-10-30
Hi,

Is it possible to maintain the specific NTFS permissions for a file on a samba share when it is copied to another location on that same samba share?

Simple question, hopefully there's a simple answer :)

---

### Post by ohzopants on 2007-10-31
I don't think so (I am really not sure).

I believe that windows handles file permissions completely differently from linux.

I think this has to do with the umask you are using when mounting the NTFS drive/partition.  All files will have those permissions by default.

---

