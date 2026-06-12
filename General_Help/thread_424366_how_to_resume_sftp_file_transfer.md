---
title: "how to resume sftp file transfer"
date: 2007-04-26
forum: General Help
---

### Post by Martin01 on 2007-04-26
Hello,

I am unable to find how to resume file transfor via sftp and command line:

I use PUT command to upload file, but when connections fails and I start again, the transfer starts from its beginning - how could I made it to check the uploaded part and then resume?

This should be possible or not?

Thanks a lot.

Martin

---

### Post by Juxi on 2008-01-07
any ideas on how I can make this work?

---

### Post by dagnabit dang doohickey on 2008-01-07
rsync is capable of resuming a partial transfer:
```
rsync --partial --progress --rsh=ssh *localfile* *remotehost:directory/*
```

---

