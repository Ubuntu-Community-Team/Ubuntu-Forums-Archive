---
title: "Question  - file manager copy &quot;timing&quot;"
date: 2021-06-17
forum: General Help
---

### Post by anneranch on 2021-06-17
I do copy of about 30000 files 
first copy from HDD to same HDD starts with ...15 minutes...
second copy same HDD to same HDD starts with  ...40 seconds
My assumption is the first copy is "saved" somewhere 
and second copy DOES NOT read the HDD again but 
copy from "somewhere"
HOWEVER taking minutes to read from HDD seems way too long

---

### Post by TheFu on 2021-06-17
Use rsync.
Lots of files, huge or tiny, has lots of overhead.  The copy wants to keep the owner, group, permissions, other ACLs, and xattrs, whenever possible. This all takes time.

Depending on the RAM in the system and how it is being used, it could be that files are in a disk buffer in RAM. RAM that isn't being used is wasted, so it gets used for I/O buffering - disk and network traffic - until some higher priority need happens.

Inside GUI file managers, some want to create thumbnails or icons for every file. This can take time.
It is difficult to understand what the issue could be since the methods used, the hardware it is on are not provided. We cannot read minds.

---

### Post by Impavidus on 2021-06-17
> **anneranch said:**
> 
My assumption is the first copy is "saved" somewhere
You are correct. The files get cached in ram, provided they're not too big.
> 
HOWEVER taking minutes to read from HDD seems way too long

That depends. You didn't mention the size of the files and whether you read them from an SSD or a spinning hard drive. In case of a spinning hard drive, copying 30000 files means 30000 times seeking the start of the file, each time taking a few centiseconds.

---

### Post by ActionParsnip on 2021-06-17
If you move data between drives a lot it may be faster to make an uncompressed archive, move that then extract the data. This can accelerate backups too. Loads of little files takes far far longer (in time) to backup than one large file of the same size.

---

### Post by anneranch on 2021-06-19
We cannot read minds.
Nobody asked you.
If the post if not clear to you , do not bother to reply or post stupid remarks.

---

### Post by anneranch on 2021-06-19
> **Impavidus said:**
> You are correct. The files get cached in ram, provided they're not too big.


That depends. You didn't mention the size of the files and whether you read them from an SSD or a spinning hard drive. In case of a spinning hard drive, copying 30000 files means 30000 times seeking the start of the file, each time taking a few centiseconds.

I am asking for time comparison - that has pretty much very little to do with actual physical size of the files.
But since you brought it up  - I am copying about 20kb  files of 500Mb and having 8Gb RAM. 

(So if I copy 2kb the time should go down to 1/10 of previous times ) . 

Between same partition on HDD connected via USB 2.0 . 
In theory - it could be done using internal HDD cache - but I do not know the size and the HDD copy time
 is still way too long, irregardless who is doing the buffering .

---

### Post by TheFu on 2021-06-19
Never mind.

---

### Post by coffeecat on 2021-06-20
Thread closed for the time being pending staff review.

**Edit:** this thread will stay closed. From the forum [Code of Conduct ]("https://ubuntuforums.org/misc.php?do=showrules"): 

> We also want this to be a place where community can develop and we can enjoy one another's company. To achieve this, we strive to maintain an atmosphere that can be enjoyed by all and we ask all members of the community to be respectful at all times. This means please use etiquette and politeness. Treat people with respect. If you do this, the rest of the code of conduct won't need more than a cursory mention.

---

