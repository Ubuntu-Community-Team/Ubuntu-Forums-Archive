---
title: "How to remove SSD icon from dock"
date: 2021-02-26
forum: General Help
---

### Post by Old Jimma on 2021-02-26
HI Community:

I added an SSD to my computer for additional storage using the disks app.

THere is an icon labled "SSD" in my dock now. 

How can I remove that icon without unmounting the SSD?

Thanks,

Old

---

### Post by TheFu on 2021-02-26
There is an option in the **gnome-disks** program that says whether the mount should be shown or not. Just saw that yesterday.

Or you can edit the line in the fstab using **sudoedit** which could be much easier. If you hadn't used gnome-disks, it is unlikely you'd have checked the box to show or unhide the mount.

---

### Post by Old Jimma on 2021-02-26
H Fu,

It is always good to get your advise!!! Thank you!

I've been using the "disks" app. It makes things easy that used t be hard!

Here his how to hide the icon in the dock:

launch disks app > click gear icon > click edit mount options > uncheck the box "show user interface"

Many thanks to Fu!!!

Old Jimma

---

### Post by TheFu on 2021-02-26
gnome-disks can help with simple mounts, but it doesn't add performance tuning options and doesn't display those options.  With EXT2/3/4, that doesn't matter. 

With NTFS, people will get ~ 30% less performance. Is that really worth the trade-off?

And the mount stuff is buried a few GUI-levels deeper than it should be, IMHO. Took me an extra 40+ seconds to find it yesterday. I was curious only. Doubt I'll ever use it.

To me, it is much easier to **sudoedit /etc/fstab** and put in the mount wanted with the options we want.

And not all systems have gnome-disks loaded which makes it less useful when trying to answer questions.  All Ubuntu systems have sudoedit.

Pros/cons in everything.

Glad you figured something out.

---

### Post by Old Jimma on 2021-02-26
Well said, Fu.

---

