---
title: "NFS not recognise NIS group/gid?"
date: 2008-05-06
forum: General Help
---

### Post by patrickst on 2008-05-06
Hi,

I just encountered a problem between NFS and NIS.

I'm having both NFS and NIS server on FreeBSD machine.

I'm using Kubuntu (I'm not asking about Kubuntu rather Linux in general) as NFS and NIS client.

The NFS client can mount network folder beautifully.
The NIS client can authenticate user, group, password, hosts, etc.

The problem:
In NFS server (FreeBSD machine), a directory is shared:
   dir:   */testdir*
   owner: *joeblack*
   group: *mib*
   permission: *drwxrwx---*

In NIS server (FreeBSD machine), *joeblack* (user), *joewhite* (user) and *mib* (group) are shared for NIS client. *joewhite* is also in the group of *mib*.

If *joeblack* login from client machine (Kubuntu), he can access */testdir*.

When *joewhite* login from client machine (Kubuntu), he doesn't have permission to accesss */testdir* eventhough the group permission of the directory is set to group read/write/executable. NOTE, *joewhite* and *joeblack* are part of *mib* group.

If another directory is created on local client machine (Kubuntu), and the permission is set similar to */testdir*, having the same owner *joeblack* and group *mib*, *joewhite* is able to access it.

The question: why *joewhite* can access local directory but not network directory, while both local and network directory are having the same permission, owner and group property?

NOTE: *joewhite*, *joeblack*, *mib*, local directory, */testdir* (network directory) are having the same UID and GID.

Cheers,

---

