---
title: "Puzzled with file systems and sizes"
date: 2007-11-09
forum: General Help
---

### Post by camini on 2007-11-09
I'm no expert with file systems and the such but am puzzled with the following situation:

I have:
1 ubuntu partition of 9GB - ext3
1 swap of 1 GB
1 data partition of 12Gb

What is weird is that in my (aMule) temporary folder (which is on my ubuntu partition - not data) I have 13GB of data files.. 
I tried to move these files to my data partition, but ubuntu told me there's not enough space (which makes sense, as 1 only have 12 gb on my data partition).

But?  How can there be a folder with 12GB data in a file system or partition that is only 9GB?

Am I missing something here?

---

### Post by geirha on 2007-11-09
what does this command display? ```
df -h
```

---

