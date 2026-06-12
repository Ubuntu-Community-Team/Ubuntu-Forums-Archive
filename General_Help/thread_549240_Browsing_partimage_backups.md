---
title: "Browsing partimage backups"
date: 2007-09-12
forum: General Help
---

### Post by Jamie Jackson on 2007-09-12
Is there a way to expand/browse partimage backups without having to restore them to a partition?

I've got old backup files: mybak.000, mybak.001, mybak.003, etc., that I want to mine for gold, then delete.

Thanks,
Jamie

---

### Post by tszanon on 2007-09-14
> **Jamie Jackson said:**
> Is there a way to expand/browse partimage backups without having to restore them to a partition?

I've got old backup files: mybak.000, mybak.001, mybak.003, etc., that I want to mine for gold, then delete.

Thanks,
Jamie
I don't know if it's possible, because I think partimage does not copy the files, I think it copies each occupied sector of the disk. So it wouldn't care if that sector is from file A or B, just the data is important.
Based on this (pure speculation), I'd say that there's no way of doing this.

---

### Post by Jamie Jackson on 2007-09-14
I'm thinking you're right.

---

### Post by Snam on 2008-01-13
I know it for sure, it is not possible yet. See the Partimage FAQ "Any hope of a browser like utility to allow restoring individual files from the archives? Like Ghost Explorer?":
[http://www.partimage.org/Partimage-FAQ#Any_hope_of_a_browser_like_utility_to_allow_restoring_individual_files_from_the_archives.3F_Like_Ghost_Explorer_.3F]("http://www.partimage.org/Partimage-FAQ#Any_hope_of_a_browser_like_utility_to_allow_restoring_individual_files_from_the_archives.3F_Like_Ghost_Explorer_.3F")

But it maybe possible in the future....!!! > "We will try to make partimage image files mountable: a driver, such as the loop one, could allow us to make an image file be a block device."

---

