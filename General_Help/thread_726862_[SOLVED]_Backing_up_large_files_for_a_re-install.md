---
title: "[SOLVED] Backing up large files for a re-install"
date: 2008-03-17
forum: General Help
---

### Post by JoshHendo on 2008-03-17
When installing my Ubuntu system, I did some partitioning I would like to change. A simple way would be to re-install.

I have a Virtual Machine file, 15GB, and I want to be able to copy it to my Ext Hard Drive, which is FAT32. Is there any way to copy this large file over without reformatting the external hard drive (that would be a pain), because I would like to re-install, but I can't loose this virtual machine.

Splitting the file could work, but I am unsure of how I would go about that.

Any help would be appreciated.

Thanks, Josh.

---

### Post by lloyd_b on 2008-03-17
> **JoshHendo said:**
> When installing my Ubuntu system, I did some partitioning I would like to change. A simple way would be to re-install.

I have a Virtual Machine file, 15GB, and I want to be able to copy it to my Ext Hard Drive, which is FAT32. Is there any way to copy this large file over without reformatting the external hard drive (that would be a pain), because I would like to re-install, but I can't loose this virtual machine.

Splitting the file could work, but I am unsure of how I would go about that.

Any help would be appreciated.

Thanks, Josh.

Open up a terminal window, and type "man split".  Give you three guesses what that command does :)

Lloyd B.

---

### Post by JoshHendo on 2008-03-17
That seems all good for what I want, but how about joining files? (I can't seem to work out how to use the join command).

Thanks! Josh.

---

### Post by lloyd_b on 2008-03-17
> **JoshHendo said:**
> That seems all good for what I want, but how about joining files? (I can't seem to work out how to use the join command).

Thanks! Josh.

The "join" command has nothing whatsoever to do with the "split" command.  The way to reassemble the file is with the "cat" command:
```
cat bigfile1 > newbigfile
cat bigfile2 >> newbigfile
cat bigfile3 >> newbigfile
cat bigfile4 >> newbigfile
```

The initial "cat bigfile1 > newbigfile" will create the file "newbigfile".  The subsequent "cat ... >> newbigfile" will append the contents of that file onto the the end of "newbigfile".

Lloyd B.

---

### Post by JoshHendo on 2008-03-17
Got it: cat prefix* > NEWFILENAME

Edit: You posted just before me (didn't see it upon refresh). Thanks.

---

### Post by lloyd_b on 2008-03-17
> **JoshHendo said:**
> Got it: cat prefix* > NEWFILENAME

Edit: You posted just before me (didn't see it upon refresh). Thanks.

That command is NOT reliable.  It depends on "prefix*" expanding into the files in the properly sorted order.  If you've got a relatively small number of files (fewer than 10), it may be fine, but once you hit 10 expect it to stop working.

For a test, "ls prefix*" and see what order the files appear in...

Lloyd B.

---

