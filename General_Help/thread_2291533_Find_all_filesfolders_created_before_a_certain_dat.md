---
title: "Find all files/folders created before a certain date?"
date: 2015-08-20
forum: General Help
---

### Post by andy146 on 2015-08-20
Hi, 

We have a samba share on an Ubuntu box (running Zentyal) that an office full of macs use. Something has happened recently and various folders now seem to have a created date of 1984 and are greyed out for Mac users, whereas Windows users can view these fine. 

My terminal skills are extremely limited and this is rather time sensitive. I'm trying to run a command/script that will first identify all of these folders within the share recursively, and then another to change these attributes.  I've managed to learn that ctime is different from what I'm looking for, but perhaps to use to stat's birth time? I've not even looked at the second part yet just trying to get identifying the files/folders out of the way first. 

Could anybody please point me in the right direction?

---

### Post by papibe on 2015-08-20
Hi andy146. Welcome to the forum ):P

A combination of 'find' and 'sort' should give provide some help.

For instance, this would create a list of filenames sorted by year of last modification:
```
find -printf "%TY %p\n" | sort -n -k1,1 > ./list.txt
```
It may take some time depending on how many files you have. If that is a problem, you may run it on the second level of the hierarchy instead of  on the root of the share.

Hope it helps. Let us know if that helps, and if you need more suggestions or details.
Regards.

---

