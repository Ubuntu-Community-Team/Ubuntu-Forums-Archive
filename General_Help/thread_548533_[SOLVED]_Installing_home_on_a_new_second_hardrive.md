---
title: "[SOLVED] Installing /home on a new second hardrive"
date: 2007-09-11
forum: General Help
---

### Post by willz06jw on 2007-09-11
Howdy,

I installed Ubuntu a while back and liked it so damn much that I have filled the hard drive to the brim (only 500 mgs left).  I do what any normal guy would do ... bummed a hard drive out of a broken computer in the corner and finally tossed the broken contraption out of the door.  

Now here is the problem:  I partitioned the drive as an "extension" in GParted and I would like to put the entire /home folder on it since it is larger than my current hard drive.  GParted says that it is unallocated.  What is the first step?  

Thanks for your help,
Will

---

### Post by merlinus on 2007-09-11
What do you by an "extension?"

You may need to create separate partitions, or at least one large one.

---

### Post by southernman on 2007-09-11
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by vanadium on 2007-09-11
I understand that you do not have the partiioning right on your second drive. You will first need to get that one properly partitioned and formatted, though. Perhaps with "extended" you mean you created an extended partition already? Since you are going to have a single partition anyway on that drive, there is no need for that. Delete it, create one primary partition filling the whole drive and format that as ext3. Then mount the partition and continue with the instructions linked to by southernman to create and install the new home partition.

---

### Post by willz06jw on 2007-09-11
Thanks guys/gals

That worked perfectly the first time!

Thanks again,
William

---

