---
title: "[SOLVED] Add user to www-data"
date: 2007-07-01
forum: General Help
---

### Post by Megaqwerty on 2007-07-01
I am trying to allow a user on my system to write to /var/www. Now, I know that all documents in there must be owned by www-data for it to show up on the net, so I have left the permissions intact. So I tried to circumvent that by doing: ```
sudo adduser <username> www-data
``` While www-data shows up as one of the groups when I do ```
groups <username>
``` The user still can't write to the directory or even cd to the directory for that matter.

Here are the permissions of /var/www:
```
drwxrw-r--  5 www-data www-data 4096 2007-06-13 20:31 www
```

Does anyone know what I did wrong?

Thanks,

Megaqwerty

---

### Post by scxtt on 2007-07-01
you can't **cd** to the directory because **/var/www** doesn't have e**x**ecute group permissions for it ... you could write a file to it, tho - according to what it says ...

what's the output of **cat /etc/group | grep $USER**?

you should have used the command **sudo useradd -G www-data $USER** which would have added you to that group, modifying your account ... not sure what your command did, almost looks like it would just add 2 users, <username> and www-data - and since both exist, probably did nothing ...

---

### Post by Megaqwerty on 2007-07-01
Thanks. **sudo chmod 774 /var/www** fixed it! 
Oh, and as for what the command did, from the Man page: ```
adduser [options] user group
``` Which added my pre-existing user to the www-data group.

Thanks again,

Megaqwerty

---

