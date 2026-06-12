---
title: "Can I restore partiton and filesystem info?"
date: 2007-05-09
forum: General Help
---

### Post by jinx099 on 2007-05-09
I had an installation of Feisty 64 installed on 2 drives in software RAID-0 (boot was RAID-1).  I foolishly wiped out the partition info for both drives without realizing that I had a semi-important file on there.  I have NOT repartitioned or reformatted the drives.

Is it possible to restore the partition and filesystem info for the drives so that I can recover the file?

---

### Post by dcstar on 2007-05-10
> **jinx099 said:**
> I had an installation of Feisty 64 installed on 2 drives in software RAID-0 (boot was RAID-1).  I foolishly wiped out the partition info for both drives without realizing that I had a semi-important file on there.  I have NOT repartitioned or reformatted the drives.

Is it possible to restore the partition and filesystem info for the drives so that I can recover the file?

Maybe, if you use a tool such as cfdisk and you can remember exactly the starting sectors of the partitions.

I believe that there are also various partition recovery tools around, you may want to do a web search for them.

---

### Post by jinx099 on 2007-05-10
> **dcstar said:**
> Maybe, if you use a tool such as cfdisk and you can remember exactly the starting sectors of the partitions.

I believe that there are also various partition recovery tools around, you may want to do a web search for them.

thanks for the suggestion, i might try that.  However, if i put in the partitions wrong, would it then be unrecoverable?  If i did recover the partition info, I'd still need to recover the filesystems.

Any more ideas?

---

### Post by jinx099 on 2007-05-13
bump

---

### Post by fragos on 2007-05-13
Use synaptic to install package "testdisk".  It claims to repair partitions of many types but I don't have any firts hand experience with it.

---

