---
title: "new partition - 6gb used??"
date: 2006-12-13
forum: General Help
---

### Post by Baji on 2006-12-13
here's my problem: I created a new ext3 partition (120gb), upon creation gparted told me 6gb was used. All I could see inside the mount was the lost+found directory which only was a few KB.

After copying my files over I still come 6gb short, and df -h gives me this strange reading:

```
/dev/hda2             120G  113G  1.3G  99% /opslag
```

120gb size, 113gb used, 1.3gb free??

my files are 112.1 GB (120,314,827,563) in total...

anyone got an idea? I could really use those 6gb...

---

### Post by taurus on 2006-12-13
5% of the space is reserved for journaling when you use ext3 filesystem...  And besides, 120GB is not really 120GB!!!

---

### Post by Baji on 2006-12-13
> **taurus said:**
> 5% of the space is reserved for journaling when you use ext3 filesystem...  And besides, 120GB is not really 120GB!!!

talking about fast answers ;)
thank you I wasn't aware of those 5%, makes sense!
but 120gb should be 120gb if its one of more partitions on a harddisk?

160gb harddisk = +/- 152gb

3 partitions + swap = 11gb + 120 gb + 19.5gb + 1.5gb = 152gb

---

