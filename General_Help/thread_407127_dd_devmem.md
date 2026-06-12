---
title: "dd /dev/mem"
date: 2007-04-11
forum: General Help
---

### Post by Andu on 2007-04-11
Ok, I'm not sure whether this is the right forum for this question, but i can't think of a better place to post it.....

I need to make an image file of /dev/mem for a program i am writing. 

I have 232Mb memory. 

When I log in as root, and use dd=/dev/mem of=dump.img  I get the following. 

dd: reading '/dev/mem': Operation not permitted
2056+0 records in
2056+0 records out
1052673 bytes (1.1MB) copied, 0.1324 seconds, 5.8 MB/s

Now.. i'm sure that this file is bigger because it goes from the system.map file, the adress of init_task is at offset (physical address) 0x331a60  and when i open the image file the offset only goes up to 0x00101000...

I need more than just 1.1MB

I'm not sure if this is because of the fact that it is 'operation not permitted' or something else... and if so, i know there is a way to get the whole thing, because i have read that it has been done.

---

### Post by Endolith on 2008-05-23
Same idea here: [http://ubuntuforums.org/showthread.php?p=5029123](http://ubuntuforums.org/showthread.php?p=5029123)

---

