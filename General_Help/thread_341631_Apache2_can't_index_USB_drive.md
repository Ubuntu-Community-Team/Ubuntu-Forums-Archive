---
title: "Apache2 can't index USB drive"
date: 2007-01-18
forum: General Help
---

### Post by chrsjav on 2007-01-18
Hello,

Is there a way to change the permissions on mounted external USB hard drives?  I haven't been able to include folders from my external hard drive in my apache2 auto-index pages, and I suspect the hard drive's permissions are to blame.

When I attempt to give read and execute access using the gnome UI, the permissions just revert back to None.  chmod -R -v 755 reports a successful change, but when I read the permissions again there was in fact no change.

There must be a simple solution.  Any ideas?  :-k

---

### Post by dcstar on 2007-01-18
> **chrsjav said:**
> Hello,

Is there a way to change the permissions on mounted external USB hard drives?  I haven't been able to include folders from my external hard drive in my apache2 auto-index pages, and I suspect the hard drive's permissions are to blame.

When I attempt to give read and execute access using the gnome UI, the permissions just revert back to None.  chmod -R -v 755 reports a successful change, but when I read the permissions again there was in fact no change.

There must be a simple solution.  Any ideas?  :-k

What filesystem is on the drive?

---

### Post by chrsjav on 2007-01-19
> **dcstar said:**
> What filesystem is on the drive?

The external is Fat32.

---

### Post by chrsjav on 2007-01-21
Essentially, I get a 403 Forbidden Error when I try to view a folder on an external drive (or a symbolic link to that folder).  This issue has totally halted development of my server :frown: 

Any ideas?

---

### Post by chrsjav on 2007-01-21
For those who stumble on this post with the same issue, a friend of mine identified the underlying problem:

Fat32 does not support *nix permissions.  Whatever user mounts it claims sole rwx rights (i.e., mod 700).

---

