---
title: "Network priviliges setup"
date: 2005-06-01
forum: General Help
---

### Post by Krank on 2005-06-01
Hello.

I have a directory called /var/archive , which I would like to share to certain users on my local network.

The users should all be able to read, write and execute files in the dir.

Files uploaded to the dir should have the user as "owner", but be changeable by all.

My work so far:

I have created a group called "remoteusers", in which I have placed the users who should have rwx access to the dir.

I have set the group ownership of the dir to "remoteusers", and set group privileges to "rwx" using chmod -R.


How do I proceed?

My main problem is, right now, that even though the users are in the "remoteusers" group, they cannot, for some reason, write to the dir. Why is this, and how can I fix it?

And how do I fix it so that all new files in the dir get the group "remoteusers"?

---

### Post by thrift on 2005-06-01
does /var/archive and not just the files under it have the correct attributes?

Is this an NFS share?

You can set the sticky bit on /var/archive for the group and own the directory to the group to be sure that all files created under it are created with the correct group name.

chmod g+s /var/archive

Hope that's helpfull

---

### Post by Krank on 2005-06-01
Both the files and the dir itself have the correct attributes.

It is not an NFS share.

Thanks for the sticky bit, though - do I need to stick a -R to make the changes to all subdirs and files of the dir?

---

### Post by thrift on 2005-06-01
If it's not NFS, does the network side of things have anything to do with this or are you testing it local?  that's the only reason i asked if it was NFS.

You don't want to use a -R with the sticky bit, that can lead to very unintended consequences on your executables.  You just want to mark the directory and subdirs with the sticky bit.

I'm having trouble understanding why users can't create files in the directory.  If the users are members of the group, and the users have logged in after they have been given membership to the group, and the directory is owned by the group, and the directory has rwx permissions for the group, anyone in the group can write to that directory.

If this is all you are trying to do, standard UNIX permissions should be adequate.

If you continue to have problems or need something more look into ACLs.

---

