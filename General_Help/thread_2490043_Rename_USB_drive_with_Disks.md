---
title: "Rename USB drive with Disks?"
date: 2023-08-20
forum: General Help
---

### Post by lou6 on 2023-08-20
Is this possible?  I know I have done it in the past but could not do it with the current release (Xubuntu 22.04.2).  Spent 30 minutes or so trying with no joy so I installed gparted and was able to rename my new drive easily.  Is this a problem with the current version of Disks (or is it something I'm doing wrong)?

Not a burning problem but I'd like to know (if some wise person has the answer).  TIA for any enlightenment :)

---

### Post by TheFu on 2023-08-21
I think it is the LABEL on the file system/partition which you want to change.  Different file systems have different tools to change the LABEL value.  I don't really trust Gnome-Disks and would recommend using **gparted** instead.  If you want a faster way and the file system is ext2/3/4, **e2label** is the command.  For NTFS, it is added with the format.

```
sudo mkntfs -Q -L $LABEL $DEV
```

Set the LABEL and the DEV variables for your needs.  I think LABELS have a 12 character limitation and certain characters aren't allowed, depending on the file system.  I tend to use 1 word, no spaces, no _ or punctuation characters to avoid hassles.  I know a hyphen works, at least for ext4 file systems.

In short, don't trust gnome-disks.

---

### Post by lou6 on 2023-08-21
Thank you.  Closing this out now.

---

