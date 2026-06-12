---
title: "How do share partitions on new 8.04"
date: 2008-06-05
forum: General Help
---

### Post by CD Baric on 2008-06-05
Hi:

I just upgraaded (new install) from 7.10 to 8.04.

I shared all my attached HDs and some partitions using a utility under the System, Administration menu in 7.10.

The problem is I have installed Samba and enabled sharing under Services BUT I can't find the utility that allows me to select which partitions to share in 8.10.

Anybody want to share?

Thanks,

Bar
(I CAN do this manually)

---

### Post by drs305 on 2008-06-05
In nautilus you can select folders and right click, properties, and enable sharing.

---

### Post by CD Baric on 2008-06-06
> **drs305 said:**
> In nautilus you can select folders and right click, properties, and enable sharing.

Thanks for the feedback.

I was able to share entire HDs and partitions with Ubuntu 7.10.

I have entire HDs and partitions I want to share, not just individual folders.

How do I share entire HDs and partitions? Where is the missing SMB/NFS sharing app?

CD Baric

---

### Post by drs305 on 2008-06-06
> **CD Baric said:**
> Thanks for the feedback.

I was able to share entire HDs and partitions with Ubuntu 7.10.

I have entire HDs and partitions I want to share, not just individual folders.

How do I share entire HDs and partitions? Where is the missing SMB/NFS sharing app?

CD Baric

I do that via nautilus as described previously. My partitions are mounted in /media (i.e. /media/data ) It shows as a folder but it is in fact the entire partition I have mounted in fstab with "defaults, user".

---

### Post by CD Baric on 2008-06-06
> **drs305 said:**
> I do that via nautilus as described previously. My partitions are mounted in /media (i.e. /media/data ) It shows as a folder but it is in fact the entire partition I have mounted in fstab with "defaults, user".

OF COURSE!

Thanks so much!

I was trying to share the HD links showing on the desktop.

I wonder what happened to the application that used to reside in the System Admin menu.

Thanks for sharing.

CD Baric

---

