---
title: "Using scp from a cron job"
date: 2007-07-31
forum: General Help
---

### Post by tim.n9puz on 2007-07-31
Once each day I would like to copy a few files from a Linux machine in one building to a machine in another building. I want to do this from a cron job so it happens automatically during the evenings. 

"scp" works fine from the command line but expects me to be there to enter a password. Is there a way to supply a password on the command line so I can run it from a script?

Tim

---

### Post by AnRa on 2007-07-31
You have to use scp in batch mode. Read [THIS](http://support.svi.nl/wiki/ScpBatchMode)! ;)

---

### Post by tim.n9puz on 2007-07-31
Excellent! Their comment "Instructions to do so are a little ambiguous..." is an understatement.

I'll give this a try tomorrow.

Tim

---

