---
title: "partition problem - I don't want to loose all data"
date: 2008-05-14
forum: General Help
---

### Post by tjk on 2008-05-14
I was getting a large number of errors when booting today -- it appeared to be a harddrive problem.  When I opened the "KDE Controls Module" it appeared that my extended partition had been renamed (and resized). This is what it read: [INDENT]Partition #4
Size: 1.0Kb
Mount Point: /proc
Type: proc
Device: proc
and it's enabled
[/INDENT]It's my understanding that the size of the extended partition is the total size of all partitions that are within it.  It amazes me that my system still boots with this problem.  How can I fix it without loosing any data?

---

### Post by sweeneytodd on 2008-05-14
might be wrong but it looks pretty damaging whatever happened as the extended partition isn't suppose to include ur root drive. I'd serously be looking at backing up ur data and reinstalling it without touching the partitioner until u have more understanding about it. select "use entire disk"

---

