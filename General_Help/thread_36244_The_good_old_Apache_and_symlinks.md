---
title: "The good old Apache and symlinks"
date: 2005-05-22
forum: General Help
---

### Post by drx on 2005-05-22
Hi,

i have an apache2 running now, and problems with symlinked folders. Into my DocumentRoot /var/www/ i put several symlinks to directories on the system.

The apache.conf and my host configuration are the default ones. Everywhere there is written for each <Directory>:

  Options FollowSymLinks

But all the symlinks produce a 404 forbidden.

The error.log says for example:
   
   Symbolic link not allowed: /var/www/d-a-s-h

This is discussed a lot on the web, but mostly the given answer is, that in the distros people use, the FollowSymLinks option is disabled by default. While i see it enabled by default in ubuntu everywhere.

"SymLinkIfOwnerMatch" also doesn't help: altho i made sure that the owner of the symlink and the actual folder is the same (can it be different with a ln -s made on the same file system?) all symlinks only produce forbidden errors.

What can i do?

Thanks again people.

---

