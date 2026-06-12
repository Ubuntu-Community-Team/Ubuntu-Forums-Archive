---
title: "cant update ubuntu anymore..."
date: 2013-03-03
forum: General Help
---

### Post by crazymonkey05 on 2013-03-03
hello i have a problem again this time i cant update ubuntu 12.04 cache anymore. it says it has failed because of a internet connection error but my connection is fine

here is the error it gives me ```
W:Failed to fetch http://ppa.launchpad.net/bimsebasse/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/bimsebasse/ppa/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/bimsebasse/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
``` and thats it any help on how to fix this would be appriciated...

---

### Post by TheFu on 2013-03-03
If you visit those locations in a browser, does it work?

What is the exact command you use?

Can there be a new proxy that is required?

---

### Post by Cheesemill on 2013-03-03
That PPA only has software for 12.10 (quantal) not 12.04 (precise), hence the errors.

You need to remove the PPA by opening the Software Sources application and unchecking it from the list.

---

### Post by gifford on 2013-03-03
12.04 is precise.

---

### Post by Cheesemill on 2013-03-03
> **gifford said:**
> 12.04 is precise.

Thanks. Fixed typo in post.

---

### Post by crazymonkey05 on 2013-03-03
thanks everyone i removed those sources and bam i can update again.

 thanks again the tread can now be closed

---

### Post by claracc on 2013-03-04
> **crazymonkey05 said:**
> thanks everyone i removed those sources and bam i can update again.

 thanks again the tread can now be closed

As you got fixed your problem, please mark the thread as solved with thread tools in the upper part of the page.

---

