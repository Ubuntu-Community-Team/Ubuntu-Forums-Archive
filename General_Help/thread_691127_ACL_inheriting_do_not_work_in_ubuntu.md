---
title: "ACL inheriting do not work in ubuntu"
date: 2008-02-08
forum: General Help
---

### Post by grof on 2008-02-08
I setup ACL on my ubuntu and it works. But it works on newly created folder and files in the folder where I set up default permissions.

When I copy some other folder to the folder with default ACL permissions, this copied folder have not permissons from folder above. On other hand do not inherited permissons from parent folder. Why?

Why this works only on newly created folders but not on copied folders?? 

If I install Dolphin into my ubuntu's GNOME, than Dolphin works well with ACL inheriting but Nautilus or Tunar do not.

If I try copy dirs and files on console, out of GNOME  with *cp* command than inheriting do not work.

So, it works only with Dolphin.

From other side, if I work in kubuntu, than works with Dolphin and Konqueror but do not with installed Nautilus or with *cp* command at console.

Now I do not understand anything...:confused:

please help how I can get inheriting with ACL in ubuntu 7.10 properly...

---

### Post by dcstar on 2008-02-09
> **grof said:**
> I setup ACL on my ubuntu and it works. But it works on newly created folder and files in the folder where I set up default permissions.

When I copy some other folder to the folder with default ACL permissions, this copied folder have not permissons from folder above. On other hand do not inherited permissons from parent folder. Why?

Why this works only on newly created folders but not on copied folders?? 

If I install Dolphin into my ubuntu's GNOME, than Dolphin works well with ACL inheriting but Nautilus or Tunar do not.

If I try copy dirs and files on console, out of GNOME  with *cp* command than inheriting do not work.

So, it works only with Dolphin.

From other side, if I work in kubuntu, than works with Dolphin and Konqueror but do not with installed Nautilus or with *cp* command at console.

Now I do not understand anything...:confused:

please help how I can get inheriting with ACL in ubuntu 7.10 properly...

```
man cp
``` will explain what happens to attributes when you use this command.

As for Nautilus, it does what it does and I don't think there is an option to change that.

---

### Post by fozzyuw on 2008-05-13
One thing I'm noticing about Linux (specifically Ubuntu) when it comes to permissions is that permissions are set once and forget.

I've been playing around with ACL's and traditional permissions (I'm new to Linux/Ubuntu administration) and if you setup ACL default permissions, only "new" directories and files will inherit the parent folders permission.

If you chance the permissions of the parent folder, the sub-folders do not appear to "recursively" update (as in, using the -R option).

This is a bit counter intuitive to me.  To me, ACL's should encompass all sub-folders/files at *any time* but they do not.  Instead, "default" rules only apply to sub-folders/files if one of two conditions are met...

A) File/Folder is created as a descended of a folder with default ACL permissions.  This created file/folder will inherit the permissions that the Ancestor folder has at the time of creation and will not change unless specifically modified by part B) below or directly with "setfacl".

B) Changes to the ACL are made with Recursive option enabled. "setfacl -R -M ugo::rwx".  The new rules will be applied to all sub-folders/files.

Note: This means that moving a folder/file into another folder hierarchy will **NOT** grant or change permissions of that folder (the one you moved) to match any "default" permissions of the parent folder(s).  The folder you moved will retain it's same permissions it's always had.  Or putting it another way, it's permissions will not change.

Example: 

I move the folder "/test" into "/var/www".  "/test" has permission "o::rwx" (anyone can read, write, execute).

"/var/www" has *default* ACL permissions "default:g:webwork:rwx,default:o::---" (only the group 'webwork' can read, write, or execute.  Others have no permissions).

After the move, the folder "/test" still has the permissions "o::rwx" it had before the move, even though it's in the "/var/www" folder now, which has default ACL permissions.  Any files in "/test" will also keep their permissions.

*IF* I created the folder "sudo mkdir /var/www/test" !THEN! the created folder will be given the same permissions as setup by the "default" ACL.

Likewise, moving a folder with default ACL permissions from the folder hierarchy will not change it's permissions.

Example:

Moving a folder "/private/test" to "/public/test" will make the folder "test" remain with it's private permissions because permissions are not inherited on moves.

In that sense, the only way to "inherit" permissions is by creating a new folder/file under an ancestor that has default permissions or using the "-R" recursive option on a parent folder to apply to all children folders.

This is how it works, it appears, for Ubuntu Linux ACL.  It's now how I expected it to work but it appears to be how it does.  I don't know enough about ACL's and Linux/Ubuntu to know if there's options you can change in the ACL package to get the functionality you want.  I do question the usefulness of ACL's with this kind of default structure.  It doesn't seem like there's much difference between ACL and traditional permissions but with added processing costs to implement the ACL.

> please help how I can get inheriting with ACL in ubuntu 7.10 properly...
Suffice it to say, it's not that ACL's are "broken", it's that ACL's don't work like you're thinking they will work.  ACL permissions do not apply to the whole "bucket" and anything that it take in/out of said bucket.  They only apply to things created in that bucket or specifically told to be applied to (through direct permission setting or using the Recursive option)

Cheers,
Fozzy

ps Feel free to enlighten me more about Ubuntu ACL's.  I cannot seem to find enough information on them, even in my 1100+ page Ubuntu book.

---

