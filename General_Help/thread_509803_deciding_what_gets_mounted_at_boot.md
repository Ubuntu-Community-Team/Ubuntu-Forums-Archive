---
title: "deciding what gets mounted at boot"
date: 2007-07-25
forum: General Help
---

### Post by vwaj on 2007-07-25
ok, so,
i am running a dual-boot machine -- vista and ubuntu.  when ubuntu starts, it automatically mounts the 3 vista ntfs partitions in /media/.  however, i do not want ubuntu to mount these partitions unless i specifically ask it to.  is there a way to control which partitions get mounted at boot?

---

### Post by logos34 on 2007-07-25
You need to edit /etc/fstab.

Take out the 'defaults' for the ntfs (vista) partitions and put in the 'noauto' (=no automount) option.  So a vista partition on, say, hda1 might look like this instead:
[B]
/dev/hda1 /media/windows ntfs user,noauto,ro 0 0[/B]

or if using ntfs-3g driver:
[B]
/dev/hda1 /media/windows ntfs-3g users,noauto,uid=1000,gid=100,umask=007 0 0[/B]

---

### Post by strabes on 2007-07-26
Why couldn't he just remove the fstab entries for the ntfs partitions altogether?

---

### Post by logos34 on 2007-07-26
> **strabes said:**
> Why couldn't he just remove the fstab entries for the ntfs partitions altogether?

Because it's easier to mount them manually if there are fstab entries with specified mount points already.  All he has to do then is:

sudo mount /dev/hda1  

and it will mount according to the fstab entry

instead of 

sudo mount -t ntfs[-3g] /dev/hdxy /media/mountpoint 

It has the virtue of being more economical, no?

---

### Post by vwaj on 2007-07-26
thanks very much logos -- that was very helpful.

---

