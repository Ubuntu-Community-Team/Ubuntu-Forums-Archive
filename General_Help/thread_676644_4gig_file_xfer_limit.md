---
title: "4gig file xfer limit?"
date: 2008-01-24
forum: General Help
---

### Post by Rondil on 2008-01-24
So my windows box has gotten infected with a rootkit. I am backing up my files and don't want to infect my backups so I partitioned up my drive and installed an older version of Ubuntu 6.06. I am using Ubuntu to do the backups to prevent the malware from crossing over to my external HD. Mostly its worked great. I have 4 iso files that are 4.4 gigs. The transfers crash at 4.0 gig. The Nautilus shell I am using gets blown away. 
I tried rsync and it has the same problem. It blows up at 93%, roughly the same point.
Are the later versions of Ubuntu suseptable to this bug?
Any workarounds?

Thanks guys :)

---

### Post by aidanr on 2008-01-24
Are you backing up to a fat32 partition? fat32 has a 4gb filesize limit.

---

### Post by Rondil on 2008-01-24
Ah thats it. I forgot about that limit. I'll have to make a seperate ntfs part then for those files. It's not Ubuntus problem at all then.
Thanks

---

