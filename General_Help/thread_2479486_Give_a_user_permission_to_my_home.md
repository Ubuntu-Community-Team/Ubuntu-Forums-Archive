---
title: "Give a user permission to my home"
date: 2022-09-26
forum: General Help
---

### Post by klapvogn on 2022-09-26
Hey,

I have a friend that need to help me organize for files and folders for me, but it's all inside my home folder, how can I archive that, without coping the stuff to his home folder?

---

### Post by vanadium on 2022-09-26
Sit together on the computer screen? Give him your account password?

---

### Post by SeijiSensei on 2022-09-26
Add the user to your group. You have an automatic group with the same name as your username.

```
sudo adduser friend_username your_groupname
```

For instance, "sudo adduser seiji bill" would add user seiji to user bill's group.

Now give the group full rights to the files in your home.

```

cd ~
chmod g+wx .

```

That grants (w)rite and e(x)ecute  privileges to the group on all your files and directories. After you're done, you might want to make your files private again by using

```

cd ~
chmod g-wx .

```

The "execute" permission means "listable" when applied to directories.  Read this if you don't have much experience with Unix permissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by klapvogn on 2022-09-26
Thx, i'll have a play with that :)

---

### Post by TheFu on 2022-09-26
You'll probably want to force the setgid bit on every directory too (in addition to the g+wx suggested above), or you could end up with his user and group owning files in your HOME, which isn't ideal.

That would be 
```
$ find ~/ -type d -exec chmod g+s {} \; 
```.
Do that before he visits your HOME and starts screwing around.  But I suspect this isn't a good idea.  The owner of the directory really needs to be the organizer of that directory or files will end up lost in nooks you never knew to look.  

Sit down together, decide on an organization together, then the issues shouldn't be too hard to resolve when they happen.  Also, having a good deep search tool, like recoll on the system for your files would be extremely helpful.  Recoll is like your own personal google, just for your storage.

---

### Post by klapvogn on 2022-09-27
Hey again!

Could I make a ```
ln -s
``` to his home dir?

the issue is that we don't live in the same city :-)

---

### Post by TheFu on 2022-09-27
That would make a link which could make it 1% easier to access, but not fix the permissions.  If you just want him to view, it might work for read-only, depending on your defaults (look up umask), but that isn't the default for Ubuntu 22.04.  If you expect the other user to have write, then you absolutely must do what was suggested above.  If you don't also do the setgid stuff, there will be a mess of mixed owners, mixed groups, and some files YOU won't be able to access, delete, move too - in your own HOME!

You really need to learn basic Unix permissions. It is the core of all Unix-like OSes  ... which is every popular OS in the solar system, except MS-Windows. Spend the 45 minutes fully engaged to learn it, practice it and try odd permission settings between 3+ different users and groups or you will never "get it."  You will likely be forever frustrated on Ubuntu or any Linux without this knowledge.

I know you didn't ask this, but allowing another user access to your HOME for write is a terrible idea. Terrible.  It would be better to move any files you want shared to a 3rd directory and set that up with a different group - a new group, that both you and he are in.  You might trust this other person ... which is fine, if they are truly trustworthy. Then just give that person sudo access and be done.  If they aren't competent enough to use sudo, then they aren't competent to have access to your HOME.  They can do all sorts of damage with just HOME access .... like make it so you can't login.

---

### Post by ne29914 on 2022-09-27
> **TheFu said:**
> 
I know you didn't ask this, but allowing another user access to your HOME for write is a terrible idea. Terrible.  It would be better to move any files you want shared to a 3rd directory and set that up with a different group - a new group, that both you and he are in.  You might trust this other person ... which is fine, if they are truly trustworthy. Then just give that person sudo access and be done.  If they aren't competent enough to use sudo, then they aren't competent to have access to your HOME.  They can do all sorts of damage with just HOME access .... like make it so you can't login.
I have to agree with TheFu here. Not a good idea.

I believe it is not used very much anymore, but such a "shared" directory already exists.
It's called $HOME/Public
On my machine, $HOME has permissions 751. Elevating $HOME/Public rights _only_ might be a solution here.

---

### Post by TheFu on 2022-09-27
[https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch03s08.html](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch03s08.html)  has the official specs on what should be in a $HOME.  They leave it open, as one of the key aspects for Unix is that users are the reason for the OS. Not much help or guidance.

The easier version of the standards is here: [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) . The simple table has been sufficient for my needs to this point. After all, even /home/ isn't a standard, which might be confusing to most users here.

~/public/ is a compromise. Seems reasonable, assuming the other user(s) don't start abusing it to get around full disk quotas.

---

### Post by #&amp;thj^% on 2022-09-27
> **TheFu said:**
> 

~/public/ is a compromise. Seems reasonable, assuming the other user(s) don't start abusing it to get around full disk quotas.

This is a good Heads Up/Warning. ;)

---

### Post by ne29914 on 2022-09-27
I don't want to impose on this thread, but I think my question. might help @klapvogn
What would it take to set up a collaborative folder ($HOME/Public)?
I imagine:
1: create a new group.
2: add collaborating users to this group.
3: set $HOME/Public to belong to this group (chown +g)
4: set $HOME/Public to have permissions 770
Does this look right?

---

### Post by TheFu on 2022-09-27
> **ne29914 said:**
> I don't want to impose on this thread, but I think my question. might help @klapvogn
What would it take to set up a collaborative folder ($HOME/Public)?
I imagine:
1: create a new group.
2: add collaborating users to this group.
3: set $HOME/Public to belong to this group (chown +g)
4: set $HOME/Public to have permissions 770
Does this look right?

I'd change to this:
3.  chgrp -R our-fancy-group ~/Public
4. chmod -R g+rw ~/Public    # to ensure all files and directories have read and write permissionf for the group, our-fancy-group
5. find  ~/Public -type d  -exec chmod g+s {} \;    # to force the setgid flag on all directories under ~/Public.

Without the setgid flag, new directories will get the primary group of the userid doing the creation.  With it, it will inherit the our-fancy-group group automatically.  Otherwise, the owner of the files which will be both users (or anyone in the group) will need to manually chgrp on files with their different gid.  Running that single 'find -exec' command, makes that all automatic.

On ~/Public/   the permissions for "other" aren't important, so ignore those, but it is very important that the owner and group look like drwxrws???

Oh ... moving files or directories under ~/Public/ doesn't alter their group or permissions. Any new files created would get the desired permissions, however.  mv works by changing the parent for an inode. That's why it is so very fast when performed on the same file system (usually same partition, but not always).

Note the 's' where the 'x' is for the group?  The 'x' is still needed, but the 's', setgid, is more important and gets shown in the "ls -al" output.
In about 50% of the posts about this, it is incorrectly called the 'sticky bit'.  That is a different flag, for a different purpose. The typical use of the sticky-bit is for /tmp/, but that isn't important.

Basic Unix permissions.

---

### Post by ne29914 on 2022-09-28
@TheFu, this is gold! Thank You.

---

### Post by TheFu on 2022-09-28
> **ne29914 said:**
> @TheFu, this is gold! Thank You.

If you search these forums for my username and "working together", you'll find examples for groups and setting up examples under /tmp/.

This is how Unix programming teams work on the same systems, in the same directories for the last  ... well, since the 1970s.  It is a well-used pattern.

---

### Post by klapvogn on 2022-09-29
Thanks for all the help :-)

---

