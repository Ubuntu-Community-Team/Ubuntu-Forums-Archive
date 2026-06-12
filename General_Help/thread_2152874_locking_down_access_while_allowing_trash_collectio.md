---
title: "locking down access while allowing trash collection"
date: 2013-06-09
forum: General Help
---

### Post by planarian on 2013-06-09
I just finished adding an fstab entry to automatically mount an NTFS partition that I only want accessible to two user accounts. Accordingly, I used the options ```
defaults,gid=1002,umask=007
``` where 1002 is the group I created for the two accounts. Unfortunately, the umask seems to have created a problem when I try to delete files in the partition: > unable to find or create trash directory

How do I tweak this in such a way that systems processes can do their thing but no *people* (beyond the two members of 1002) can access the partition?

Thanks.

---

### Post by gordintoronto on 2013-06-09
I have no answer to your question, but I would be very surprised if other users were blocked from mounting the partition, just by clicking on "329 GB Filesystem", or whatever it is.

---

### Post by planarian on 2013-06-10
> I would be very surprised if other users were blocked from mounting the partition

What's so surprising about restricting access with fstab? Except for the problem I've described, it works fine. I've tested it.

---

### Post by gordintoronto on 2013-06-10
Interesting, thanks.

---

