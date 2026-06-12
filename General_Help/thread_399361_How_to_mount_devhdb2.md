---
title: "How to mount /dev/hdb2/"
date: 2007-04-02
forum: General Help
---

### Post by bobcat68 on 2007-04-02
I had both secondary partitions okay when I used dapper but then I started from scratch and formatted both hard drives so as to swap them and dapper did not want to play. Seeing I had a DVD for edgy here I am.

GParted finds the /dev/hdb2 (fat32, flags = lda, status = unmounted) and all I need is a simple instruction to mount it. 

Yes, I've searched the various help files and forums but there were too many options I did not understand.

I love ubuntu to little bits but will not be upgrading until I have a better handle on edgy.
:confused:

bobcat68

---

### Post by Stephen Howard on 2007-04-02
Something like this will do it:

mount /dev/hdb2   /some-directory-where-you-want-it-to-appear

---

### Post by Stephen Howard on 2007-04-02
oh, and if you want it permanently mounted at boot then edit /etc/fstab as needed.

---

