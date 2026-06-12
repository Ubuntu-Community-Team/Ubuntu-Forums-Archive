---
title: "Couldn't find any package whose name or description matched &quot;linux-headers-uname -r&quot;"
date: 2007-08-03
forum: General Help
---

### Post by Hxsrmeng on 2007-08-03
I am installing a vmware on my computer. The host is Ubuntu 7.04. 

The first step, I just want to make a good experiment by

aptitude install linux-headers'-uname -r',
but it shows:
"
Couldn't find any package whose name or description matched "linux-headers-uname -r"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
"

I tried to update my packages repositories
etc/apt/sources.list,
aptitude update
aptitude upgrade,

but the error message doesn't change. 
What should I do? Thanks

==============================
Sorry, the fellow up, Actually I still don't know what's wrong.
============================

Funny, and then I used
apt-get install linux-headers-`uname -r` build-essential xinetd
it worked.

ANd then, I used 
aptitude install linux-headers-`uname -r` build-essential xinetd
it worked!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by machoo02 on 2007-08-03
The problem is that in the first case, you used a single quote ( ' ), and in the second case you used a backtick ( ` ).  Notice the difference in the two characters.  In the shell, whatever is between the single quotes is taken as literal values, whereas whatever is between the backticks is seen as a command, and the output of that command is put in place of the backticks.

---

### Post by ThrobbingBrain66 on 2007-08-03
This:> aptitude install linux-headers'-uname -r'
should look like this:
```
aptitude install linux-headers-`uname -r`
```

---

