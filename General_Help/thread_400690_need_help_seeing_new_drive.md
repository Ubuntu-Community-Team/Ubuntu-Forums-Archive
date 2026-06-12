---
title: "need help seeing new drive"
date: 2007-04-03
forum: General Help
---

### Post by rh9 on 2007-04-03
I had a drive die & reloaded Ubuntu 6lts on new drive. Most all is well there. 
 
I came off Red Hat 9. I mounted the Red Hat drive as a slave to the new Ubuntu master drive. Though my user account can see the drive, it can't view the contents - shows Root as the user. 
 
Objective: view/copy user data from Red had drive to new Ubuntu master drive. Reformat Red Hat drive as additional storage or backup. I need to be able to view & move files from the Red hat drive to the main Ubuntu drive. 
 
I've gone to terminal, switched to root/admin user, via SU. gave the command: chown [user] hdb. The terminal returns for the next/other commands, but nothing has changed, and I still can't view the contents of the new drive. 
 
How can I view/move files from the old to the new drive. I'll worry about reformatting the old drive after I gain access to the old files.

---

### Post by taurus on 2007-04-03
From a terminal, run

```
gksudo nautilus
```

Now, you can view your slave drive.

---

### Post by rh9 on 2007-04-05
Taurus, Many Thanks. 
 
I've not been able to try it yet - I've lost 2 WD 80gb drives in the last two days (just loving life, I am). I appreciate your kindness.

---

