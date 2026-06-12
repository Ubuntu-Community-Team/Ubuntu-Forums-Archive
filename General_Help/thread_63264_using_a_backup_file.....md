---
title: "using a backup file...."
date: 2005-09-07
forum: General Help
---

### Post by floyd27 on 2005-09-07
Hi..
I find myself backing up alot of config files (because tyhe guide says too)
ut what does this do?

I have messed up ati drivers a bunch of times and just reformat to slove to prob..
What good was backign up the file ?

How do i access it or use it to fix things?
thanx

---

### Post by kkvenkit on 2005-09-08
The Ubuntu Guide makes a backup of the file by copying the file (*cp*) to the same directory/filename but with a _backup suffix. 

To copy a file you run: *cp <src file> <dest file>*.

So say you ran *cp /etc/fstab /etc/fstab_backup*. And now you want to restore the backup. You would run *cp /etc/fstab_backup /etc/fstab*.

Because cp, by default, overwrites files without prompting I suggest following this part of the guide: [http://www.ubuntuguide.org/#promptbeforeremovaloverwrittenconsole](http://www.ubuntuguide.org/#promptbeforeremovaloverwrittenconsole)

---

