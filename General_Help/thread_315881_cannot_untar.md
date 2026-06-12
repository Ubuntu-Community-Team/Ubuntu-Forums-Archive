---
title: "cannot untar"
date: 2006-12-09
forum: General Help
---

### Post by veli on 2006-12-09
I'm trying to untar some "tar" files and it seems that they are not properly extracted. For example, I was extracting the last kernel from kernel.org, and some of the files were extracted, but the output of some was "no such directory" or like that. After the unsuccessful extracting I didn't have access to any administrative processes, gksu nautilus, synaptic, users etc didn't work. I had to reboot.

I tested the untar process by running following test.tar.gz file and from terminal I got:

$ tar -xzf test.tar.gz
tar: test.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I don't know what I've done, I noticed that some time ago when I wasn't able to install StarOffice 8, which I've installed many times before. 

Any idea how to restore the things. I reinstall the tar and dpgk packages, same result.

---

### Post by meng on 2006-12-09
It says there's no such file
ls test.tar.gz
will confirm if the file is there or not.

---

### Post by veli on 2006-12-09
I extracted the file by right click "extract here". It worked.

The problem is however with the big tar files. I did untar the kernel source tar file in the same way, but it extracted only about 20 MB. This extraction would have given you about 300 MB untarred file.

Same happened with StarOffice 8. Incomplete extracting of big TAR files - I'd named this problem.

---

