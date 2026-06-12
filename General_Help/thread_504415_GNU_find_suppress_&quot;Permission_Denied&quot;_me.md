---
title: "GNU find: suppress &quot;Permission Denied&quot; messages"
date: 2007-07-19
forum: General Help
---

### Post by charlie. on 2007-07-19
How do I suppress "permission denied" messages from GNU find?

Here's an example: I want to find "postgres.h", somewhere in my file system. If I run the command as the super user:

sudo find / -name "postgres.h"

... all is fine and well.

What if I can't run it as root? I know that the file does exist in a directory that I can read, but...

find / -name "postgres.h"

... throws up thousands of "permission denied" messages for directories that mean nothing to me, such as "/proc/26313/task/26313/fd". (It still finds the file, however.)

I want to instruct find to skip these directories, without obscuring the useful output with useless error messages.

Any ideas?

---

### Post by needtolookatascreenshot on 2007-07-19
[http://ubuntuforums.org/showthread.php?t=519877](http://ubuntuforums.org/showthread.php?t=519877)

---

### Post by charlie. on 2007-07-19
That works. Cool.

I knew that you could re-direct the std. error, but I just never thought to use it here. (Duh!)

Thanks.

---

### Post by vjones777 on 2008-01-08
> **needtolookatascreenshot said:**
> [http://ubuntuforums.org/showthread.php?t=519877](http://ubuntuforums.org/showthread.php?t=519877)

I think that link may have been a typo.  I found this post... [http://ubuntuforums.org/showpost.php?p=3556838&postcount=2]("http://ubuntuforums.org/showpost.php?p=3556838&postcount=2")?

---

