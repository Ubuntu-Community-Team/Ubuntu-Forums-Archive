---
title: "Apache symlink permission issues"
date: 2007-07-20
forum: General Help
---

### Post by srunni on 2007-07-20
Hi,

I'm trying to symlink some folders from my home directory to /var/www , so that they can be accessed through Apache without copying the actual files to /var/www . However, when I try to do so, I get a 403 (forbidden). I know that the files being symlinked to are readable by ALL users and that when I put actual files in /var/www there are no problems at all. Does anyone know how to fix this?

Thanks in advance for the help!

---

### Post by az on 2007-07-20
Why don't you just point the DocumentRoot to a folder in your home drive?  Just make sure the folder is world-readable, but not writeable or executable by anyone but you.

---

### Post by srunni on 2007-07-21
Alright, I'll give that a shot. I never thought about doing that instead of using symlinks. Thanks a lot!

---

### Post by matth45 on 2008-01-08
I know this is an old topic, but in case you *really* want to use symlinks instead of moving your document root, you need to make the entire path to the symlink target readable to the apache user.

For example, if my document root is /var/www/html and I want to link to a directory called /foo/bar/baz, and I create a link /var/www/html/baz -> /foo/bar/baz, then it is not enough to set the permissions of baz to be readable by your apache user. /foo must be readable and executable by apache, and /foo/bar must be readable and executable by apache.

There are many ways to set this up, changing ownership, group membership, permissions, etc... but one way might look like this:

# ls -ld /foo
drwxr-xr-x 1 ... /foo
# ls -ld /foo/bar
drwxr-xr-x 1 ... /foo/bar

etc...

---

