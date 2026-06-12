---
title: "How to make a file untouchable by a specific user?"
date: 2019-12-29
forum: General Help
---

### Post by mangonels on 2019-12-29
I have a restricted access SFTP only user, this user has control over a certain directory only, and all of it's contents.

In this directory there's a file and a folder I DON'T want the user to:
- Download
- Delete
- Read
- Modify
- Move

Basically, I want the file and the folder to be untouchable (I don't care if they're seen or not), ONLY for this user. All other contents within the restricted access directory are, and should, still be freely usable however the account sees fit.

Both are meant for monitoring, and if removed or tampered with it would affect security.

Ideas? Thanks in advance :)

---

### Post by aljames2 on 2019-12-29
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

File permission 700 grants file owner access only.
```
chmod 700 filename
```

If your users are known, you could create a group that includes all the members that “should” have access And grant a group level permission, then exclude everyone else.
```
chmod 750 filename
```

In addition you could make the file hidden by placing a dot in front.
```
.filename
```

---

### Post by TheFu on 2019-12-29
Need to see the permissions on the specific directory AND the parent directory to it.  Showing a sample of files and permissions for files _inside_ the specific directory would help too.

In Unix, there are permission for read, write, and execute by the owner, group and everyone else ("other").  You can use any of those different parts to control what the specific user may or may not do.

It is very important that all others you want to allow access be innumerated as well.  None makes it easier, but some can work too.  Additionally, the userids and groups which create the files would need to be known.  This is critical for log files.

aljames2 has the right idea for simple needs. Hopefully this is sufficient for the solution. Most of the time, it should be, but there are some other complications which might arise.

---

### Post by mangonels on 2019-12-30
I tried chmod 700 before I even asked this question, but it somehow doesn't stop the file from being deleted and/or downloaded in filezilla.
In fact, as long as it wasn't deleted, moved or modified by the restricted user, that would be enough. The most important thing is that it doesn't get altered in any way, so that it can function reliably.

Your second option (creating a special group for access) is just another way of doing the same, but with a diferent outcome I presume. In theory your first chmod proposal should be enough, but I can still somehow remove the file and/or folder with the limited access account, which shouldn't be capable of doing that... (I'll try this again, but I'm pretty sure, not 100%, it's as I describe).
Even if you didn't propose this option as an alternative, It's not necesary in my case, since the owner still has access and that's enough for me.

Finally, hiding the file won't be enough, since you can show hidden files with filezilla, and then delete it since permission 700 isn't enough protection.

---

### Post by Holger_Gehrke on 2019-12-30
Deleting a file doesn't require any permissions on the file. Removing a filename needs write permission on the directory containing the file since names are stored in the directory. A file really has no 'actual' name, it's identity is tied to the inode that stores the permissions, owner, group, block list, the various timestamps and the number of hard links; the directories store names and inode numbers; hard links are names in directories and the blocks allocated to the file are freed when the hard link count in the inode reaches zero.

Holger

---

### Post by mangonels on 2019-12-30
My case may not be that simple. The folder I want to protect is being modified by the same file I want to protect (a .jar plugin), but I don't know what user that would count as (Is a jar editing a folder even considered a user? How can I find out?). So I guess there may be a 3rd account that could need access.

two accounts only should have control over the file and folder:
- root
- network

one account should not:
- build

I don't care if other accounts have access or not. (I probably won't make any more, but otherwise I still wouldn't care)

The parent folder where the .jar file and the folder are contained is currently 777 (I may need it like this, otherwise other files and folders within won't be addable by the limited access account), a folder within, I want protected, is 770, and the .jar file I want protected is 644

Note: I can still remove the folder, and the file, with these permissions, with an account that isn't the owner, nor belongs to the right group. At least I cannot rewrite their names with this limited account.

**Edit: **I just noticed build is the owner of the jar file, I'll put that in order and try what aljames suggested again...

Happy new year all, and thanks for the help.

---

### Post by mangonels on 2019-12-30
In the jar file's case (perm 644), the owner is now network, but it can still be deleted and moved to other directories. Would be nice to stop that.
I'm guessing I should also change the parent folder's permissions, but won't that affect the use of the rest of files and folders within? And uploads... etc.

I don't think I'll do any more experimenting (I've done enough without results) until you guys have any other suggestions.

---

### Post by The Cog on 2019-12-30
Being able to delete a file depends on being able to write to the containing directory. In general anyone with write access to a directory can create/delete any file in the directory, even if they don't have read accessto the file. I think that if you set the sticky bit on the directory, things change so that only the file owner (normally the creator) can delete a file in the directory. [https://www.linuxnix.com/sticky-bit-set-linux/](https://www.linuxnix.com/sticky-bit-set-linux/)
This may do what you want, although you still have to use normal access control to prevent the user read/writing the file.

---

### Post by TheFu on 2019-12-30
Rather than describing permissions, please, please, please, post the output from **ls -al** for the parent directory and the subdirs where this issue lies.  We are experts at reading that and don't have to spend 10 minutes trying to understand what you are trying to really say.

sftp follows the normal unix permissions. PERIOD.  Every process runs under both an effective userid and an effective groupid.  PERIOD.  The userid and group membership (not just the effective group, for any groups that userid is a member of will only have the permissions provided through Unix for any files on a Unix file system or accessed using Unix-native network protocols like NFS.  Samba and CIFS ignore those permissions completely.

To prevent any users from having access to a directory, do this:
* on the parent directory, **sudo chown root:root /path/to/parent; sudo chmod 700 /path/to/parent **
* on the specific directory, **sudo chown root:root /path/to/parent/subdir ; sudo chmod 700 /path/to/parent/subdir**
Once those 4 commands are run, nobody but root running a root process has access.

There are all sorts of ways to allow other userids to write into a directory, but not read the list of files.
**sudo chmod g+wx /path/to/parent/subdir ** then you'll want to **chgrp** on the subdir so that only the members of some specific group you want to have write can write, but not any others.  This might require creating a new group and adding userids as members.

The first link provided by aljames2     [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)  should cover this, but nothing will replace spending 45 minutes in a temporary directory, say /tmp/foo/, opening 3 terminals, creating 3 new userids, 2 groups, mixing and matching which users are in which groups and literally using chown, chmod to try out every possible combination of permissions for all 32-bits.
chmod 000 /tmp/foo
chmod 100 /tmp/foo
chmod 200 /tmp/foo
chmod 300 /tmp/foo
chmod 400 /tmp/foo
chmod 500 /tmp/foo
chmod 600 /tmp/foo
chmod 700 /tmp/foo
chmod 110 /tmp/foo
chmod 120 /tmp/foo
.... 
chmod 776 /tmp/foo
chmod 777 /tmp/foo
you get the idea.
A light-bulb of understanding should happen around 751  that will make you go aaaaaah.  Then you can test settings that you think will specifically work ....or not.  For every setting, use all 3 userids to see what access is possible.  Do the same for files inside the foo directory.  Mix and match groups, owners, permissions. Another aaaaaah moment will happen.

The file ownership, like for a jar file, has ZERO to do with the userid running it, beyond that userid having read access for it.  Processes access files. In a terminal, the process trying to read a file is probably bash.  There is a userid running bash and that userid is where the access permission limits begin.  A jar file is normally accessed by tomcat or jboss or weblogic.  Each of those would be running under a specific userid, which must have read access to the jar file(s) needed.  Those processes would nominally need write access to any application specific log files - or they could use a socket (file or network) to pass logging information to another process (like syslog or rsyslog or journalclt) for logging. 

But all of this follows pretty basic, consistent, Unix permissions which are the cornerstone for all popular non-Microsoft OSes world-wide. Learning this stuff isn't a waste of time.

Or you can spend hours, days, weeks, months being frustrated.

---

### Post by mangonels on 2020-01-01
I'll do it your way. And let what I found out be known after that. :-)
I already have a local ubuntu VM for that purpose. Should be interesting.

---

