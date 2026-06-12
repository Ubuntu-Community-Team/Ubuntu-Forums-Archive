---
title: "Samba password file"
date: 2008-06-09
forum: General Help
---

### Post by ctrlER on 2008-06-09
Hi.
I've searched my hard drive but I'm not finding the file where samba is keeping its passwords. I'm trying to sync my user passwords with my samba passwords (and I'm getting nowhere) and in the process of doing that I search for it and couldn't find it.
Can anyone help me with that?

Thanks.

---

### Post by HalPomeranz on 2008-06-09
The default Samba configuration on my Hardy system puts the password database in /var/lib/samba/passdb.tdb.  Note that this is a binary database, not a flat text file, so you won't just be able to copy password entries from your /etc/shadow file into passdb.tdb.  

You can tell Samba to use a text file by setting the "passdb backend" parameter in /etc/samba/smb.conf.  But Samba uses a different password hashing algorithm from the one in /etc/shadow, so you wouldn't be able to just copy entries from one file to another anyway.

What you have to do is edit your smb.conf file and set "unix password sync = yes" and then tell your users to change their passwords using the smbpasswd command instead of the usual passwd command.  I know of no way to sync your existing user account passwords with the Samba password database other than forcing a change to all user passwords via smbpasswd (whether your users do it themselves or you do it for them).

---

### Post by ctrlER on 2008-06-09
Thanks! Very complete response.

---

