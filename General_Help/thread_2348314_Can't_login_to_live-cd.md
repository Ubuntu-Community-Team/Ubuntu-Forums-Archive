---
title: "Can't login to live-cd"
date: 2017-01-02
forum: General Help
---

### Post by David_Partridge on 2017-01-02
I left my userid intact in the copied /etc/passwd when building the live-cd, and when I booted I was offered a login prompt for that userid, but I was told my password was wrong :/

Is that to be expected?

Thanks
Dave

---

### Post by kyknos12 on 2017-01-02
The passwords can be found in /etc/shadow, not /etc/passwd

---

### Post by David_Partridge on 2017-01-03
Yes indeed, I did know that :).  

The problem was that it would seem that rsync didn't copy /etc/shadow to the work area :o. 

Manually copying it and rebuilding the iso solved that.
Dave

---

