---
title: "Hardy: apt-get remove problem (slocate)"
date: 2008-04-30
forum: General Help
---

### Post by MarnickV on 2008-04-30
Hello,

Today I wanted to run an OpenSSH-server on my macbook with Ubuntu Hardy on it. I noticed I didn't have the package, so I went on installing it with "sudo apt-get install openssh-server".

However, the installation aborts with the message:

"Removing slocate...
/usr/sbin/delgroup: `<username>` still hass `slocate` as their primary group!
dpkg: error processing slocate (--remove):
subprocess prost-removal script returned error exit status 7
Errors were encountered while processing:
 slocate
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Why the delgroup thing? How should I fix this?

Thanks!

---

### Post by Monicker on 2008-04-30
delgroup is a command to remove groups from the system.  Groups are part of the access control system.  For example, some distros of linux have a games group, which a user must be in to use programs in the /usr/games directory.  You can also add groups using the addgroup program.

I'm not sure what the package manager is trying to do in your case, but you can view which groups exist on your system, and the members of those groups, by looking at the /etc/group file.

---

