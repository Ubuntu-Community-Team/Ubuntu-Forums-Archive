---
title: "Permissions issue"
date: 2007-11-16
forum: General Help
---

### Post by rmadd on 2007-11-16
I am mounting a external hard drive on Ku. 7.10, I have the drive mounted and on my desktop, when I try to open the properties folder, permissions I receive the following message: You are not the owner, so you can't change these permissions. I am the only one using this computer and I installed Kubuntu on this machine, I used the following command to change from "root:root to my user name, still didn't work

 sudo chown (User Name); users  /media/backup
I would appreciate your help. Thanks

---

### Post by notquitemichael on 2007-11-16
perhaps not the 'cleanest' way of doing it, but using
kdsu konqueror
then right clicking on the drive in /media or /mount and choosing properties > to setting permissions to the normal user is a quick fix.
n.b. i haven't used kde since kubuntu dapper, so you may need to adlib around these instructions, but hopefully it's enough to get you on your way.

---

### Post by taurus on 2007-11-16
What filesystem is that external drive?  And by the way, it's **[COLOR="Blue"]:[/COLOR]** not **[COLOR="Blue"];[/COLOR]** if you want to change both owner and group.

```
sudo chown *username***[COLOR="Blue"]:[/COLOR]***username* /media/backup
```

---

### Post by MrFSL on 2007-11-16
...furthermore, if you want to change ownership of all the contents of the drive you would want to probably include a ***-R***

```
sudo chown -R user:group /media/backup
```

---

### Post by Goon007 on 2007-11-21
I am having a similar issue. Any help will be appreciated.

I have a drive that I am unable to write to. I have tried
```
 sudo chown username:username /media/sdd1
```

I get the following result....

```

username@username-tower:~$ sudo chown username:username /media/sdd1
chown: changing ownership of `/media/sdd1': Operation not permitted
```

Here is ls -la /media (the bolded drives are the ones I need -r -w access to, they are also formated as fat32)

```

drwxrwxrwx  9 username username  4096 2007-11-21 16:55 .
drwxr-xr-x 21 root    root     4096 2007-11-09 20:26 ..
lrwxrwxrwx  1 root    root        6 2007-11-09 20:08 cdrom -> cdrom0
drwxrwxrwx  2 root    root     4096 2007-11-09 20:08 cdrom0
lrwxrwxrwx  1 root    root        7 2007-11-09 20:08 floppy -> floppy0
drwxrwxrwx  2 root    root     4096 2007-11-09 20:08 floppy0
-rw-rw-rw-  1 root    root        0 2007-11-21 16:55 .hal-mtab
drwxrwxrwx 10 username username  4096 2007-11-17 02:49 sdb1
drwxrwxrwx 16 username username 24576 2007-11-20 20:55 sdc1
[B]drwxr-xr-x 10 root    root    16384 1969-12-31 17:00 sdd1
drwxr-xr-x  3 root    root    16384 1969-12-31 17:00 sde1[/B]
drwxrwxrwx  6 username username  4096 2007-11-16 23:24 sdf1

```

---

### Post by Goon007 on 2007-11-22
This fixed it for me.

[http://yoonkit.blogspot.com/2007/09/preserving-time-stamps-on-fat32-copies.html](http://yoonkit.blogspot.com/2007/09/preserving-time-stamps-on-fat32-copies.html)

---

