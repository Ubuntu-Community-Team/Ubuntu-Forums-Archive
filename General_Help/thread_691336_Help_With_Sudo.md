---
title: "Help With Sudo"
date: 2008-02-08
forum: General Help
---

### Post by MaxDrown on 2008-02-08
```
max@milton:/var/www$ sudo mkdir /var/www/wiki
max@milton:/var/www$ ls -al /var/www/wiki
ls: /var/www/wiki: No such file or directory
```

What am I doing wrong?

---

### Post by TheBoat on 2008-02-08
are you able to enter the new directory?> cd wiki

---

### Post by MaxDrown on 2008-02-08
Nope. It acts like it creates the directory, but it doesn't actually create it.

---

### Post by taurus on 2008-02-08
When you ran "sudo mkdir /var/www/wiki" from a terminal, did it even ask you to enter your password?

What's the output of this command from a terminal?

```
id
```

---

### Post by MaxDrown on 2008-02-08
```
max@milton:~$ ll /var
total 48
drwxr-xr-x 14 root     root     4096 2007-11-14 06:18 .
drwxr-xr-x 21 root     root     4096 2007-11-14 06:19 ..
drwxr-xr-x  2 root     root     4096 2007-11-15 06:25 backups
drwxr-xr-x 10 root     root     4096 2007-11-14 06:18 cache
drwxr-xr-x 25 root     root     4096 2007-11-14 06:19 lib
drwxrwsr-x  2 root     staff    4096 2007-10-08 05:47 local
drwxrwxrwt  3 root     root       60 2008-01-13 07:40 lock
drwxr-xr-x 12 root     root     4096 2008-02-08 06:25 log
drwxrwsr-x  2 root     mail     4096 2007-11-14 06:02 mail
drwxr-xr-x  2 root     root     4096 2007-11-14 06:02 opt
drwxr-xr-x 13 root     root      420 2008-02-08 12:28 run
drwxr-xr-x  5 root     root     4096 2007-11-14 06:18 spool
drwxrwxrwt  2 root     root     4096 2008-02-08 12:35 tmp
drwxr-xr-x  2 www-data www-data 4096 2007-11-28 14:36 www
max@milton:~$ ll /var/www
total 12
drwxr-xr-x  2 www-data www-data 4096 2007-11-28 14:36 .
drwxr-xr-x 14 root     root     4096 2007-11-14 06:18 ..
-rw-r--r--  1 www-data www-data   85 2007-11-28 14:36 index.html
```

I can't create anything in that directory using sudo (files or directories). I also can't create anything using my user, max, which is in the www-data group.

---

### Post by TheBoat on 2008-02-08
but after the sudo command does it ask you to enter a password?

---

### Post by MaxDrown on 2008-02-08
```
max@milton:~$ id
uid=1000(max) gid=1000(max) groups=33(www-data),1000(max)
```

I don't think it did ask me for a password, come to think of it.

---

### Post by taurus on 2008-02-08
> **MaxDrown said:**
> ```
max@milton:~$ ll /var
total 48
drwxr-xr-x 14 root     root     4096 2007-11-14 06:18 .
drwxr-xr-x 21 root     root     4096 2007-11-14 06:19 ..
drwxr-xr-x  2 root     root     4096 2007-11-15 06:25 backups
drwxr-xr-x 10 root     root     4096 2007-11-14 06:18 cache
drwxr-xr-x 25 root     root     4096 2007-11-14 06:19 lib
drwxrwsr-x  2 root     staff    4096 2007-10-08 05:47 local
drwxrwxrwt  3 root     root       60 2008-01-13 07:40 lock
drwxr-xr-x 12 root     root     4096 2008-02-08 06:25 log
drwxrwsr-x  2 root     mail     4096 2007-11-14 06:02 mail
drwxr-xr-x  2 root     root     4096 2007-11-14 06:02 opt
drwxr-xr-x 13 root     root      420 2008-02-08 12:28 run
drwxr-xr-x  5 root     root     4096 2007-11-14 06:18 spool
drwxrwxrwt  2 root     root     4096 2008-02-08 12:35 tmp
[COLOR="Blue"]drwxr-xr-x  2 www-data www-data 4096 2007-11-28 14:36 www[/COLOR]
max@milton:~$ ll /var/www
total 12
drwxr-xr-x  2 www-data www-data 4096 2007-11-28 14:36 .
drwxr-xr-x 14 root     root     4096 2007-11-14 06:18 ..
-rw-r--r--  1 www-data www-data   85 2007-11-28 14:36 index.html
```

I can't create anything in that directory using sudo (files or directories). I also can't create anything using my user, max, which is in the www-data group.

If you are looking at the permissions for www, you see that only owner www-data can write to it.  Anybody else, including group www-data, can only read and execute from it.

---

### Post by taurus on 2008-02-08
> **MaxDrown said:**
> ```
max@milton:~$ id
uid=1000(max) gid=1000(max) groups=33(www-data),1000(max)
```

I don't think it did ask me for a password, come to think of it.

And since you don't belong to group admin, you cannot run sudo.  That is why it wouldn't create /var/www/wiki because you don't have permission to use sudo.

So, you need to boot into recovery mode from GRUB menu and add yourself, max, to group admin in /etc/group.

```
useradd admin max
```
And while you are at it, change the permissions of /var/www so group www-data can write to it as well.

```
chmod -R 775 /var/www
```
Now, reboot and see if you can write to /var/www as max, belonging to group www-data.

```
shutdown -r now
```

---

### Post by MaxDrown on 2008-02-08
Ok. Will try when I get home. Odd that I'm not in admin group already. I am in all my other boxes. This is the only ubuntu-server box I have, so maybe it handles the first user differently?

---

### Post by MaxDrown on 2008-02-08
That worked! Thanks for taking the time to help me out.

---

