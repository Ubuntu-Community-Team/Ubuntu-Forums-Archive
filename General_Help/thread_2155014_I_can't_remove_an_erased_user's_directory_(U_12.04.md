---
title: "I can't remove an erased user's directory (U 12.04)"
date: 2013-06-16
forum: General Help
---

### Post by rva1945 on 2013-06-16
I had created "ubuntuuser", now it's gone (I erased the user) but his folder remains, and I can't remove it. rmdir ubuntuuser doesn't work (Permission denied)

sudo ... ( Directory not empty)

sudo rmdir ubuntuuser --ignore-fail-on-non-empty (nothing happens, no message but directory is not removed).

If I right-click on the folder (Nautilus), now the owner is 1003 - user #1003 (?)

Group: 1004 (?)

And the Folder access options are disabled.

So? How can I erase that folder?

---

### Post by lisati on 2013-06-16
The safest way of removing a user's home directory is via an option on the "deluser" command. For the example you gave, it would be:
```
deluser --remove-home ubuntuuser
```

There is another way, which requires special care, because it could result in accidental loss of data.

---

### Post by Impavidus on 2013-06-16
You'll have to delete all contents of the directory before you can delete the directory itself. The quick way is```
sudo rm -r /home/ubuntuuser
```Be careful, one additional space can wipe your entire system.

PS: The save way would be lisati's suggestion, but I don't know whether that still works after you already deleted the user.

---

### Post by rva1945 on 2013-06-16
> **lisati said:**
> The safest way of removing a user's home directory is via an option on the "deluser" command. For the example you gave, it would be:
```
deluser --remove-home ubuntuuser
```

There is another way, which requires special care, because it could result in accidental loss of data.

The problem is that the user ubuntuuser doesn't exist anymore, so I get this message: The user `ubuntuuser' does not exist.

---

### Post by lisati on 2013-06-16
> **rva1945 said:**
> The problem is that the user ubuntuuser doesn't exist anymore, so I get this message: The user `ubuntuuser' does not exist.
The other way I had in mind is very similar to Impavidus's suggestion. Care is needed, because a simple typo can cause accidental loss of data.

---

