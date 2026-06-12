---
title: "Logging in as root, but using USB"
date: 2012-12-30
forum: General Help
---

### Post by anon_private on 2012-12-30
I am using Lunbuntu on a USB.

I do not login.

So how can I login as root.

For example, I tried to use fsck and received a message that I need to login as root.

---

### Post by anon_private on 2012-12-30
I would like to use fsck to repair the FAT file on a USB that also contains the Lubuntu 12.10 OS (not yet working). I believe that the FAT needs a repair before I can use 12.10.

I am using Lubuntu 12.04 (on another USB) and cannot get fsck to run, because I need to login as root.

Can anyone help?

---

### Post by Wim Sturkenboom on 2012-12-30
Just put sudo in front of the command.

E.g.
```

sudo somecommand

```

---

### Post by coffeecat on 2012-12-30
Same issue - threads merged.

---

### Post by haqking on 2012-12-30
Read [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

---

