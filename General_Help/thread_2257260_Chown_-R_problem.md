---
title: "Chown -R problem"
date: 2014-12-18
forum: General Help
---

### Post by dagring on 2014-12-18
I have a folder with lots of files. I have copied them from a Windows server. When I have them on my ubuntu box I need to change permissions to the files. I have used the chown -R command to change owner, but it seems the group and others are not affected by this comand. 

$ sudo chown -R dag /home/dag/RecordedTV

Does somebody have a suggestion on how I shall alter det command so it includes group and others?

Dag R

---

### Post by steeldriver on 2014-12-18
You can specify both user and group to the chown command as *username:groupname* e.g.

```

sudo chown -R dag:dag /home/dag/RecordedTV

```

or you can change the group separately using chgrp

```

chgrp -R dag /home/dag/RecordedTV

```

You can't change "others" - they're just any IDs that do not match user or group.

---

### Post by dagring on 2014-12-18
That did the trick. Is it so that a user with a certain set of priviliges automatically becom a group with the same priviliges?

Dag R

---

### Post by bab1 on 2014-12-18
> **dagring said:**
> Is it so that a user with a certain set of priviliges automatically becom a group with the same priviliges?

Dag R
No.  You have to add users to the group you want.  Any files that are created in those directories are owned by user:user unless you set the suid or sgid bit on the parent directory.  Most folks that need inheritance use the group inheritance bit (sgid) with a common group for the involved users.

---

