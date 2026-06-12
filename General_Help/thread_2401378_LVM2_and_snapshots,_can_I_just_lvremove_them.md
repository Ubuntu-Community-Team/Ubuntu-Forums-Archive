---
title: "LVM2 and snapshots, can I just lvremove them?"
date: 2018-09-17
forum: General Help
---

### Post by uniquename2 on 2018-09-17
I have a large LVM volume, and I made two snapshots. The snapshots have since gone "INACTIVE" because they filled up. The system is otherwise running normally.

I have found documentation on LVM a bit confusing, my question is this:

After I don't need the snapshots anymore (as I understand it they're now worthless anyway since they filled up) I can just use lvremove to get rid of them, right? This won't like, roll back the disk to before the snapshots or anything? Is it really that simple and safe?

This is on Ubuntu 18.04.1. Thanks for any help.

---

### Post by Dennis N on 2018-09-17
If they fill up, they can't be used. So, you have to monitor them and increase the snapshot size if necessary. You can remove it using the **lvremove** command. No effect on original lv.
 
```
sudo lvremove /dev/vg_name/snapshot_name
```

---

### Post by Tadaen_Sylvermane on 2018-09-17
For a snapshot to have an effect on an active volume you would need ```
lvconvert --merge /dev/$VG/$WORKINGVOL
```

---

