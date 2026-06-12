---
title: "How to check mounted filesystem for errors"
date: 2007-12-07
forum: General Help
---

### Post by usien on 2007-12-07
How can a mounted filesystem be checked for errors?

---

### Post by Emerzen on 2007-12-07
Post in error.

---

### Post by rsambuca on 2007-12-07
You can't really do it while it is mounted.  You can boot up from the liveCD and run the check, though.

---

### Post by atlfalcons866 on 2007-12-07
DONT FSCK A MOUNTED VOLUME

it will corrupt the partition. Boot the live cd then run fsck with the volume umounted.

---

### Post by Emerzen on 2007-12-07
They're right and my manual is wrong.  If it's not the root filesystem you could unmount it before hand, if it is then you'll need a cd.

---

