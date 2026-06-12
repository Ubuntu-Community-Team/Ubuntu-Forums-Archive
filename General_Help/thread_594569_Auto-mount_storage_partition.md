---
title: "Auto-mount storage partition"
date: 2007-10-28
forum: General Help
---

### Post by stomponthis on 2007-10-28
Every time I go to access my storage partition it prompts me for my password.
Is there a way to disable this prompt so I have can make it automatically mount.
And how would I automatically mount it?
I change the owner to my user, and gave myself the permissions for it.

```
drwx------ 17 bilbo root 16384 1970-01-01 12:00 disk
```

Any help would be appreciated... THANKS!

---

### Post by dcstar on 2007-10-28
> **stomponthis said:**
> Every time I go to access my storage partition it prompts me for my password.
Is there a way to disable this prompt so I have can make it automatically mount.
And how would I automatically mount it?
I change the owner to my user, and gave myself the permissions for it.

```
drwx------ 17 bilbo root 16384 1970-01-01 12:00 disk
```

Any help would be appreciated... THANKS!

Install the **pysdm** package, it will add the entries to your /etc/fstab file for you (System-Administration-Storage Device Manager).

---

### Post by stomponthis on 2007-10-28
Hmmm that didn't seem to do anything?
Here is a part of the /etc/fstab.
```
# /dev/sda1
UUID=9f23cd92-7579-42c4-9311-034c529a799c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=359bf385-e2d6-4d41-9be1-80a06d3be84d none            swap    sw              0       0

```
There was no sda3 which is my storage partition>?
It is formatted in ext2, is that the right format for a storage partition?

Thanks for the time all :)

---

