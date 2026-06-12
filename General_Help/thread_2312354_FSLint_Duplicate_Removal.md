---
title: "FSLint Duplicate Removal"
date: 2016-02-03
forum: General Help
---

### Post by stevemid on 2016-02-03
I'm having the same problem. I installed FSlint.  It works beautifully in identifying duplicates and selecting same for deletion.  However the delete function does not delete the files. It was suggested elsewhere that running the program as root would solve this problem (ie by downloading gksu). Then the command from the proper directory would be: gksudo fslint-gui  This also does not solve the problem for me.

---

### Post by Vladlenin5000 on 2016-02-03
Where exactly are those duplicates you can't delete? If not in your userspace then **leave them alone**. 'nough said.

---

### Post by stevemid on 2016-02-06
> **Vladlenin5000 said:**
> Where exactly are those duplicates you can't delete? If not in your userspace then **leave them alone**. 'nough said.

For me, these duplicates are in /home/music   They were in a very large set of almost 3000 duplicate mp3 files.  FSlint would delete small subsets of the total but just would ignore the request to delete all the dups selected via the selection criteria.

---

