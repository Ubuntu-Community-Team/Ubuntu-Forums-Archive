---
title: "Formating a external..."
date: 2008-05-25
forum: General Help
---

### Post by Tom--d on 2008-05-25
I have an external harddrive. 250GB.

I want to format it. But don't know what to. 

It will need to work out of the box for windows and Linux.

I do not want ntfs as it reminds me of Windows >.>


On the external will be a backup of my Home folder. With lots of films on it. 

I was thinking fat32. Whats the pros and cons? 

Any other suggestions?

Thanks, 
Tom :)

---

### Post by bwhite82 on 2008-05-25
Fat32 has file-size limitations. I would stick with NTFS. Formatting can be accomplished with gparted (in the repos).

-Cheers

---

### Post by Tom--d on 2008-05-25
Yeah.. I know how to format :) 

Just picking which one. 

You think NTFS?
Whats your reasons?

---

### Post by bwhite82 on 2008-05-25
> **Tom--d said:**
> 
Whats your reasons?

Because of the 4GB file size limit imposed on fat32. And also because NTFS has compatibility between Linux and Windows.

---

### Post by bodhi.zazen on 2008-05-25
IMO FAT is best as it is supported out of the box by both OS.

Next is NTFS Linux support for ntfs is very good, but not perfect.

you can install a driver on windows for ext2 or ext3. ext3 is not fully supported, so #3 is ext2 and #4 ext3.

---

### Post by Tom--d on 2008-05-25
Thank you for your replies.

I think I will format it to NTFS. 
This way I can have over 4gb file size's and support on both OS.

---

