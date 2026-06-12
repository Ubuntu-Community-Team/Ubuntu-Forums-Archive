---
title: "OpenAFS (*not* Arla)"
date: 2005-10-11
forum: General Help
---

### Post by senseiwa on 2005-10-11
Hi!

I'm trying to get openafs (client) work on ubuntu 5.04, not Arla, just plain good old OpenAFS. Currently, openafs is supported at version 1.2.13 by ubuntu, which is probably NOT compatible with 2.6.x kernels. There were patches for that, but I'm not sure they're all applied. That's because I get a (critical) error on make-kpkg modules_image:

configure: error: no available sys_call_table access method

Is anyone using openafs client? How?

Thanks!

---

### Post by a9dfasd9 on 2005-10-24
I really need to get openafs running on breezy as well.  I've installed openafs-client and friends to no avail.

I ran make-kpkg to build the openafs-modules package for my kernel, and the module seems to load okay, however when I do /etc/init.d/openafs-client start or just run afsd nothing works.  Running afsd give me something about not being able to mount at /afs.

If anyone has this working, I'd really appreciate some help...

---

### Post by krugger on 2006-12-10
OpenAFS is known to work with previous versions, so you know it is possible.

Breezy - Make sure you have the breezy backport repositories in your sources.list as there have been backports for breezy.

Dapper - Should work fine if not with a 2.6.17 or higher kernel.
[http://www.ubuntuforums.org/showthread.php?t=264992&highlight=openafs]("http://www.ubuntuforums.org/showthread.php?t=264992&highlight=openafs")

Edgy - OpenAFS 1.4.1 is incompatible with kernel 2.6.17 or higher, so you need 1.4.2 which currently is only available for feisty.

Other things:

/etc/openafs - that is where the configs are
ThisCell - where you are going to be authenticated

In some places you don't have remote AFS, because the firewall prevent it.
Be aware what is the version of Kerberos your are authenticating against.

---

