---
title: "how to set root's password in a script"
date: 2019-04-29
forum: General Help
---

### Post by Skaperen on 2019-04-29
i need to set root's password for some tools that are asking for one.

however, i need to do this in a script, not interactively, because this is being done as part of the setup in an AWS EC2 instance being carried out by a user data script.

the passwd command has no option for this in its man page.  any suggestions?

---

### Post by TheFu on 2019-04-30
Have you tried using **expect**?
I haven't used it in decades, but the killer app for it was changing passwords on many systems.

---

### Post by sisco311 on 2019-04-30
chpasswd should do the trick:
```
echo "root:password" | sudo chpasswd
```

---

### Post by Skaperen on 2019-05-01
having decided it was a bad idea to include clear passwords in EC2 user data or in S3 files that user data script would download, i decided it would be better to send the already encrypted/salted password and have this script just update [FONT=courier new]/etc/shadow[/FONT] directly.

---

### Post by fu7650eo on 2019-05-01
I would use [COLOR=#000000][FONT=&quot]echo "root:password" | sudo chpasswd[/FONT][/COLOR]

---

