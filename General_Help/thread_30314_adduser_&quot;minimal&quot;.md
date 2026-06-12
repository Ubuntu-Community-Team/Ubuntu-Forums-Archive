---
title: "adduser &quot;minimal&quot;"
date: 2005-04-28
forum: General Help
---

### Post by bassMonkey on 2005-04-28
Ok,
so the task would be to create a user without a homedir and without permission to login. It's only for accessing samba shares from 2 windows xp workstations. Read the useradd manpages but it didn't make me much wiser...  :?
Suggestions?

---

### Post by accuser on 2005-04-28
> $ sudo useradd -g group -p password -s /bin/false username

Replace group with the name of the group that the user should belong to, password with the users password, and username with the users username.

The -s option sets the login shell, in this case /bin/false which prevents the user from loggin in.

---

### Post by bassMonkey on 2005-04-28
I've done some research: how about doing a passwd -l 'username' to disable the account instead and is there any harm in setting the homedir to /dev/null/ ??

and is it still possible to use the account in question after the -l operation as a samba account but with a different password for samba?

---

