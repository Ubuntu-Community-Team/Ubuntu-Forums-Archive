---
title: "Need help reinstalling postgresql-8.2 (init.d/* &amp; /var/lib/* gone)"
date: 2007-11-25
forum: General Help
---

### Post by mikecrowe on 2007-11-25
Hi folks, 

Tried installing gforge (big mistake).  Through the various attempts, I now don't have postgresql on my system.

apt-get install postgresql-8.2 seems to work, but no init.d script, nor no /var/lib/postgres files

dpkg-reconfigure --force postgresql-8.2 seems to work, but nothing

What am I missing here?  I know it's something stupid, but I can't see what.

---

### Post by Spudgy on 2008-01-30
I'm having a similar problem. I uninstalled postgresql a while ago and deleted the extra files /etc/postgresql* /etc/init.d/postgesql and /var/lib/postgresql

Now I've reinstalled the packages but it hasn't created those files again. No init.d script. No config or data directories and there's no initdb so I can't do it myself.

The installed packages were:
postgresql
postgresql-8.2
postgresql-client-8.2
postgresql-client-common
postgresql-common
libpq5
pgadmin3
pgadmin3-data

What package contains the init script and how do I get it to create it's initial database?

---

### Post by Spudgy on 2008-02-01
So nobody knows? Does that mean I'd have to completely reinstall ubuntu just to get postgresql working again?

---

### Post by Spudgy on 2008-02-04
I guess nobody reads this forum. Anyway, I got my answer by posting in another one

[http://ubuntuforums.org/showthread.php?p=4265121](http://ubuntuforums.org/showthread.php?p=4265121)

---

