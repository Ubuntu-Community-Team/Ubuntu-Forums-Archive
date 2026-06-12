---
title: "Can't chgrp"
date: 2007-04-06
forum: General Help
---

### Post by dalrympm on 2007-04-06
I've just intalled 6.0.6 Server edition and I've run into a problem where I can't chgrp. for some reason.  It's quite frustrating and I can't fathom what could be causing it.  Here is an example of what I'm running into:

```
mike@trillian:~$ cd /var/
mike@trillian:/var$ ls -al
total 48
drwxr-xr-x 14 root root  4096 2007-04-05 23:45 .
drwxr-xr-x 21 root root  4096 2007-04-05 15:38 ..
drwxr-xr-x  2 root root  4096 2007-04-05 15:33 backups
drwxr-xr-x  8 root root  4096 2007-04-05 23:30 cache
drwxr-xr-x  3 root root  4096 2007-04-05 23:45 cvsroot
drwxr-xr-x 15 root root  4096 2007-04-05 23:30 lib
...
mike@trillian:/var$ sudo chgrp -R cvs cvsroot
mike@trillian:/var$ ls -al
total 48
drwxr-xr-x 14 root root  4096 2007-04-05 23:45 .
drwxr-xr-x 21 root root  4096 2007-04-05 15:38 ..
drwxr-xr-x  2 root root  4096 2007-04-05 15:33 backups
drwxr-xr-x  8 root root  4096 2007-04-05 23:30 cache
drwxr-xr-x  3 root root  4096 2007-04-05 23:45 cvsroot
drwxr-xr-x 15 root root  4096 2007-04-05 23:30 lib
...
mike@trillian:/var$ 
```

I'm really not sure what I'm doing wrong here but it sure seems like it should work... it has on every other Linux platform I've used.  I'm just coming off old Fedora Core 4.

Any help would be greatly appreciated.

---

### Post by heimo on 2007-04-06
Seems really strange. I'd try to use strace to get any kind of hints what might be wrong.
```
sudo strace chgrp -R cvs cvsroot
```

---

### Post by dalrympm on 2007-04-06
I think I figured out what happened.  I added myself to a new group using the incorrect flag and therefore removed myself from the admin group.  I was then unable to effectively become root to make my requisite changes.  I have to say that I think it's a bug that it never complained about not having enough permissions.

A helpful post that got me looking in the right direction is [here.]("http://www.psychocats.net/ubuntu/sudo")

---

