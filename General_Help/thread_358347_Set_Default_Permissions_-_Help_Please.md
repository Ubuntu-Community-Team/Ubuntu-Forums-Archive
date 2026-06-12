---
title: "Set Default Permissions - Help Please"
date: 2007-02-10
forum: General Help
---

### Post by elgrandeburro on 2007-02-10
I apologize if this is a basic question, but I haven't been able to figure it out, nor discover a workable answer while searching.

Is it possible to force a set of default permissions on all files and folders that are created on a particular drive?

What I'm trying to do is use an additional hard drive (locally attached) to share files between local users.  No matter what user creates a file or folder on this voume, all other users will need to be able to read, write, execute, and delete those items as necessary.

My fstab has the volume setup in the following way:

 /dev/sda1 /sharedfiles ext3 auto,users,exec,rw 0 0

The mount point has the read, write and execute flags checked for all three groups (owner, group, others).  I have the uid and gid checked as well.

I realize I can from time to time go and manually run various chmod and chown commands to accomplish this, but isn't there someway of setting this up without needing to do that?

Thanks much, especially if this is an obvious question/answer.

---

### Post by kidders on 2007-02-10
Hi there,

This question isn't as basic as you might think ... the answer has two parts, really.

**Hardwiring file ownership**
Imagine you have a group of users called "webedit" that need to be able to arbitrarily read/write/create/delete web pages. Normally, when one of them creates a file, not only does he own it, but its group permission will be set to his primary group, which could quite easily be a private one (ie one of which he is the only member). Yuk.

Solution:

[LIST=1]
[*]As root, "chgrp -R webedit" the web directory.
[*]Do a "chmod g+rwx" on it, if necessary.
[*]Set the directory's sgid bit with "chmod g+s /path/to/wherever"
[/LIST]

Now, any file created in that directory will be owned by the "webedit" group, no matter who puts it there.

**Controlling default permissions**
Since any user who owns something can usually tinker with its permissions, this isn't essential, but can still be convenient. Newly created files are assigned a default set of permissions based on a thing called a "umask", which specifies the permission bits a file ***doesn't*** have. Right now, my umask is 0022, which means that, by default, files/directories I create will be world readable and executable/traversable.

Solution:

To control default permissions for new files, set your users' umasks to something sensible.


I hope that helps.

---

