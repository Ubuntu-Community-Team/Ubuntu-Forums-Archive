---
title: "How to share partitons on a ftp server?"
date: 2008-02-29
forum: General Help
---

### Post by apricot on 2008-02-29
Recently i installed proftpd and gproftpd. I have set up ftp and http server with dynamic IP address on DynDNS. The servers are running fine, but the problem is that i want to share partitons or/and other directories than /var/ftp, which is set up by default.

Is this somehow possible?
The second question is; is it possible to make a symlink of the partition/directory in my /var/ftp that i will be able to access from network, cause i managed to make a symlink, but it is not accessable from network, only from my PC with nautilus.

Thank you.

---

### Post by banewman on 2008-02-29
You might be better off with ssh for that.
:)

---

### Post by apricot on 2008-02-29
ok, i managed, i mounted the point on /var/ftp/hda5.

Now the question is how to enable read privileges for that point for anonymous user, 'cause when i log like anonymous i can get only the /var/ftp directory listed, but do not have permission for opening /var/ftp/hda5

Help, please!?

---

