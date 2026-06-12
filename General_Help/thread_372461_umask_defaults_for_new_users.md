---
title: "umask defaults for new users"
date: 2007-02-28
forum: General Help
---

### Post by Steve Smith on 2007-02-28
I'm trying to stop home directories of new users being group- and world- readable.  I could set umask in /etc/login.defs, but am I right in saying that doesn't affect ssh logins?

Where do I set it so it affects everything?

Steve :)

[b]Edit:

Can I use this with Ubuntu?
[http://packages.debian.org/stable/admin/libpam-umask](http://packages.debian.org/stable/admin/libpam-umask)
[/b]

---

### Post by WW on 2007-02-28
You don't have to use the Debian package.  It is available in Ubuntu, in the universe repository:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libpam-umask&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libpam-umask&searchon=names&subword=1&version=all&release=all)
(I don't know anything about using it, so I can't really answer your question.)

---

### Post by Steve Smith on 2007-02-28
Thanks, but it's in universe, so I'm still not sure if it's a good idea!

---

