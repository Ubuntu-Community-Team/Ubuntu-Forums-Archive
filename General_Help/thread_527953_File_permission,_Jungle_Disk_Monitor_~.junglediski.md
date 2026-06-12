---
title: "File permission, Jungle Disk Monitor: ~/.junglediskinstance"
date: 2007-08-17
forum: General Help
---

### Post by onestep on 2007-08-17
Being the inquisitive nOOb that I am I was playing around with file permissions in my Home folder. Now when I run Junglediskmonitor I get the following error message; 
 
"Lock file '/home/onestep/.junglediskinstance' has incorrect permissions." 
 
What should the correct permissions be for this file?

---

### Post by jamvegan on 2007-08-17
Lock files are usually 0600 (-rw-------).  Deleting the lock file would probably also fix the problem.

---

