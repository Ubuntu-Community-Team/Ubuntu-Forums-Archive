---
title: "changing ubuntu from 6.06 to 7.04"
date: 2007-06-23
forum: General Help
---

### Post by linux noooob on 2007-06-23
ok so besides having ubuntu i have xubuntu and i was wondering if i went into xubuntu uninstall ubuntu 6.06 then install ubuntu 7.04 the newly installed ubuntu 7.04 would have all of the same installed software and partitions as ubuntu 6.06.

also what is the comands?

---

### Post by shadows85 on 2007-06-23
> **linux noooob said:**
> ok so besides having ubuntu i have xubuntu and i was wondering if i went into xubuntu uninstall ubuntu 6.06 then install ubuntu 7.04 the newly installed ubuntu 7.04 would have all of the same installed software and partitions as ubuntu 6.06.

also what is the comands?

What do you mean? As in update from live cd, or straight from the internet?

I updated from 6.06 to 7.04 through internet btw.

Put this in the terminal: 
```
gksu "update-manager -c"
```

But you will need to update 6.06 to 6.10 to 7.04

---

### Post by qpieus on 2007-06-23
It sounds like you want to upgrade from v6.06 to v7.04. unfortunately, you cannot directly upgrade from 6.06 to 7.04 because upgrades only work for the next sequential release. So, you could upgrade from 6.06 to 6.10, then upgrade from 6.10 to 7.04 and theoretically keep all of you setting and installed programs. You really can't "uninstall" 6.06 as you said in your post. You CAN just install 7.04 right over your old installation. In this case, though, you'll have a fresh install of 7.04 and you'll need to reinstall apps you want. You also mention partitions. The partitions won't change as long as you select the manual partion option during installation and don't change any partitions.

Here's a link about upgrades from old versions:

[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion?highlight=%28upgrade%29](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion?highlight=%28upgrade%29)

Here's a link about upgrading in general:

[https://help.ubuntu.com/community/UpgradeNotes?highlight=%28upgrade%29](https://help.ubuntu.com/community/UpgradeNotes?highlight=%28upgrade%29)

---

### Post by shadows85 on 2007-06-23
EDIT: I removed this post just read the second one.

---

### Post by linux noooob on 2007-06-23
it keeps saying that 3rd part chanels are blocked and then it says file a bug report?? what did i do? it says that libwnck18 is broken or unmet dependencys

---

