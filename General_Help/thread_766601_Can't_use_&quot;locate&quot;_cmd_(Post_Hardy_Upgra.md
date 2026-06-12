---
title: "Can't use &quot;locate&quot; cmd (Post Hardy Upgrade)"
date: 2008-04-25
forum: General Help
---

### Post by haelen on 2008-04-25
Hi,

I've just tried using "locate" on the command line and get this:

*locate: can not open `/var/lib/mlocate/mlocate.db': No such file or directory*

This is after an otherwise smooth and uneventful upgrade to Hardy.


TIA,
Tim

---

### Post by nedkelly on 2008-04-25
I have the same problem



EDIT
I found a solution to the problem. Run the command ```
sudo updatedb
``` in a terminal and you should be able to use "locate again"

---

### Post by pholden on 2008-04-25
Same here, my account doesn't seem to have any write permissions on the /var/lib/mlocate directory... maybe that's it?

```
[pholden@my-computer ~]$ ls -al /var/lib/mlocate/
total 8
drwxr-xr-x  2 root root 4096 2008-03-08 18:22 .
drwxr-xr-x 59 root root 4096 2008-04-25 11:24 ..
```
Running *updatedb* causes a similar error message.

---

### Post by lizzard on 2008-04-25
It seems "locate" isn't installed by default. ```
sudo aptitude install locate
``` should resolve the problem.

---

### Post by bollix47 on 2008-04-25
Try opening a terminal (Applications > Accessories > Terminal) and copy and paste the following into it:

```
sudo ln -sf /etc/alternatives/locate /usr/bin/mlocate  
```

If it already exists but points to something different you can remove it first and try the ln command again.

```
sudo rm /etc/alternatives/locate
```

---

