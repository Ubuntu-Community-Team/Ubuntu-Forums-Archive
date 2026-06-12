---
title: "sudo wildcard issue"
date: 2008-03-03
forum: General Help
---

### Post by omrsafetyo on 2008-03-03
I have an issue with the way sudo works.

When you use the following command:
```

sudo grep mysearch /home/accounting/*/.profile

```
to grep all .profiles belonging to people in the accounting group, you receive the error:

grep: 0652-033 Cannot open /home/mu0811/*/.profile.

This is because of a permission issue, in which the shell expands the wildcard (*) before it issues the sudo command.  

Because of this, I therefore do not have the root access required to view the files in these directories.  When it tries to resolve all of the filenames that it later needs to grep once the command is issued, I do not have permission to do the required listing.  

This is a problem.

Other than adding the "sh" command to the sudoers list, and forking a new shell everytime I want to run a command - can anyone think of a workaround?

---

### Post by lloyd_b on 2008-03-04
Basically, you want wildcard expansion to occur, but you want it to be done after assuming root authority.  The only way to make this happen is to invoke a sub shell via the sudo:
```
sudo sh -c "grep mysearch /home/accounting/*/.profile"
```

Lloyd B.

---

### Post by kuja on 2008-03-04
It seems it gives me much stranger behavior - rather than trying to expand it and subsequently giving me an error, it doesn't try to expand it at all and tells me the path doesn't exist!

A very strange quirk you've run upon. I wonder why it behaves so differently for you.

---

### Post by Distro Jockey on 2008-03-04
A possible workaround:
**sudo su**
This gives you a root prompt, then do what you need to do.

---

### Post by omrsafetyo on 2008-03-04
kuja - that is actually the same error I get (basically) - assuming you are trying to search a directory you don't have permissions for.

If you don't have permissions to "ls" the directories, and subsequently view which files need to be searched by the grep command, it essentially doesn't find the files to grep, and therefore tells you it can't find the files.

It could, if only you had permissions.

I'm avoiding the two proposed work-arounds, which I was already aware of.

Thanks for the suggestions, but they are not quite what I was looking for.

Currently I am su'ing to a generic account in the workgroup I need to search for - this gives me the access I need, but is kind of a hassle.  I am looking for a simple way to make this work with sudo - without forking a new shell, and without logging the user in as root.

---

### Post by PapaNerd on 2008-03-04
So what you are saying is that (A) the original login from which you are doing the sudo is NOT part of the accounting group of users, (B) the permissions on the accounting department directories are no longer set to the default (755), (C) the permissions on the accounting department .profile files are no longer set to the default (644), or some combination thereof.  From a security standpoint, this is good.  

Therefore, if you want to do admin work in the home directories, the login from which you are executing your grep commands needs to be trusted by the accounting department logins.  This means either becoming root, creating a separate accounting admin account (your current work around), or having another admin login be trusted by the accounting department logins.  The easiest way to do this might be just adding your original admin login to the accounting group in the /etc/group file, and then making sure the group permissions of the directories/files belonging to the accounting department users are set properly (at least 750 on directories and 640 on files if you want read access).

---

### Post by omrsafetyo on 2008-03-04
I agree with you PapaNerd.  The proposed solution is the best solution.

The problem is adding (and subsequently maintaining) the groups for each of these demi-admin roles - as there are currently over 90 groups.  We are currently looking into the security issue - we have 3 users who actually log in as root (ill-advised, I know), and 5 support users who currently use sudo to accomplish anything that requires root access.

As I said, approximately 90 groups - across 3 servers (well, 2 servers, and 1 server cluster) for which the sudoers list is currently updated; and 5 users that need limited administrative, yet unrestricted access to their folders.

Its not just the home folders either - we have databases and binaries for each group which are also maintained through sudo access by these 5 users.  None of these groups should be able to interact with (read: be able to know they exist) the others folders.  Currently this works.

We will eventually look into the security issue more seriously, but until someone can commit the time to figure out exactly how that will work, and be maintained - we are looking into work arounds.  If it can't be done, we still have the workable solution of the group adminisration user which we su to.  I was just looking for a better solution for some simple tasks.

Thanks

---

### Post by PapaNerd on 2008-03-05
omrsafetyo:  Been there, done that (both in smaller and larger scales)!

Keeping user groups apart always results in a bit more admin time, no matter whether you select the added security on one/several machine(s), or go with implementing many servers.  One approach you might want to consider is setting up a xen server so that you can create multiple instances of virtual servers all on the same physical server (or cluster).

---

