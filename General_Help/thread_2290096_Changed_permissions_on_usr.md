---
title: "Changed permissions on /usr"
date: 2015-08-09
forum: General Help
---

### Post by tolou.sobh on 2015-08-09
> **Denis_Uyeda said:**
> 
  I accidentally changed the whole /usr/lib permissions... =\
Don't do this! I am having a lot of problems now.




**I changed it too,,,](*,)](*,)](*,) how can I rectify it?**

---

### Post by TheFu on 2015-08-09
a) restore from a backup that actually retains owner, group and permissions.
b) reinstall
c) perform a fresh install somewhere else and look at the file permissions on that other install, then make the permissions match on the problem system

Lots of options.

Most should be root:root and 755 for directories.  There are a few exceptions, so that isn't the total answer. Sorry.

Messing with file/directory permissions outside your HOME is a really bad idea.  It also has HUGE system security impacts.  Things are the way they are for a reason. Before you change any permissions, be certain you understand what it really means.

---

