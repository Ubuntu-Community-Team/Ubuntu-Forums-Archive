---
title: "Writing to 2 directories at once (through a symlink or something)"
date: 2013-08-15
forum: General Help
---

### Post by quickk on 2013-08-15
Hi everyone, 

     I would like to know if there is a way to write to two directories at once.   I have 2 separate networked folders that I connect to using the webdav protocol.   Both folders should have identical content (say data1 and data2).   Instead of uploading files to data1 and then doing the exact same thing again for the data2, I would like to be able to just copy files to one place and have them automatically go to data1+data2.   

For example, if I could make a symlink point to both data1 and data2 at the same time, this would work.   But I don't think that symlinks can do this.   

Any ideas?

---

### Post by ajgreeny on 2013-08-15
Try ```
ln -s *foldername* data1
ln -s *foldername* data2
``` one by one.  That will mean that any file you actually save to foldername will also appear in both data1 and data2.

If you do this when data1 and data2 already exist you will see *foldername* in data1 and data2; if data1 and data2 do not already exist they will me made and contain the files already in *foldername *and as you add files to* foldername *they will also appear in data1 and data2.

I hope that is clear; try it out and you'll quickly see what I mean.

---

### Post by quickk on 2013-08-15
Thanks for the help ajgreeny.    I don't think that this works though.   If I do as you say, I will just get two symlinks called data1 and data2 that point to foldername, and the the data would reside in foldername.   I want the reverse.   I would like foldername to point to the two separate folders data1 and data2 (the data in this case resides in data1 and a copy in data2).   

For some background: I am managing a course that has two names say PHY101 and ENG101.   I regularly upload documents to the course's webpage (Blackboard, if that means anything).   Unfortunately, both PHY101 and ENG101 have separate webpages even though they are really the same course.   I would like to simply be able to upload documents to the one "symlink" that points to the webdav mount for each course.   I hope this makes sense!

---

