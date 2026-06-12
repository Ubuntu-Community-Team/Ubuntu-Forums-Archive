---
title: "Purge old kernel images in /boot ?"
date: 2006-08-03
forum: General Help
---

### Post by rwilliams on 2006-08-03
I notice that kernel image updates always leave behind the old System Map-xxxxx, vmlinuz-xxxx, initrd-xxx, abi-xxxxx, and config-xxxx files.

Presumably it's safe to delete these older files after a while ?

Thanks
Rich

---

### Post by mlind on 2006-08-03
Yep, it's safe to remove those if actual package has been removed.
Use *aptitude purge package* or *dpkg -P package*

---

### Post by rwilliams on 2006-08-03
I ended up using synaptic - which worked perfectly.
Thanks for pointing me in the right direction.
R.

---

### Post by tedrogers on 2007-02-13
Thanks....I was wondering this too.

Simplest way for me was to go into Synapatic and search for 2.6.17-10-generic (the older version at the time when 2.6.17-11-generic was released) and then choose MARK FOR COMPLETE REMOVAL. 

Apply it and bang...bosh...100MB more disk space! ;)

---

