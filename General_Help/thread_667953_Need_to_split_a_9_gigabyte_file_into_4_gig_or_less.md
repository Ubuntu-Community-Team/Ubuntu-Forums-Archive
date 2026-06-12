---
title: "Need to split a 9 gigabyte file into 4 gig or less chunks"
date: 2008-01-14
forum: General Help
---

### Post by diablo75 on 2008-01-14
I have a virtual machine on a clients computer that was not configured to split the VM hard drive volume files into 2 GB chunks upon creation.  So now, we have a 9 gigabyte file that represents the hard drive of this virtual machine, and we want to move it over to another ubuntu computer using blank DVD's. What's a fast, easy way to do this?

---

### Post by benanzo on 2008-01-14
You can split a large file into smaller pieces with the **split** utility.  For instance to to split your 9GB file into 2GB (or less) chunks you would do:
```
split -b 2048m BigFile
```

This will create four 2GB files called 'xaa, xab, xac' etc and one 1GB file.

To rejoin them after you've transferred to a new disk use **cat**.

First change to the directory with all the xaa, xab etc files in it and do:
```
cat x* >> BigFile
```

That will add each file sequentially to the end of BigFile so you will eventually get the exact same file as before.  You can verify it but checking the md5sum before and after splitting/joining.

---

