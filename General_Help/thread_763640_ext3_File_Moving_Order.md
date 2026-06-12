---
title: "ext3 File Moving Order"
date: 2008-04-23
forum: General Help
---

### Post by baudelaire on 2008-04-23
Hey, guys.  What is the deal with the file moving order in ext3 (at least I think it's ext3)?  In windows it copied file in alphabetical and numerical order in each folder through each file -- however I've noticed in Ubuntu with ext3 it copies the folders in order, but when it comes to a folder it will often copy the files within the folder out of order.  Why is this?  Does this questions make sense? Many thanks in advance on helping me solve this strange phenomenon.

---

### Post by ryanhaigh on 2008-04-23
I think you will find this is not ext3 specific but rather specific to whatever you are using to copy the files, for example if you copy a bunch of file/directories with nautilus (gnomes/ubuntus default file manager) the order may be different to that you would see using dolphin (kde fm) or cp from the terminal. As far as the reason for it, perhaps nautilus/whatever your using uses the timestamps on the files, the more recently the file has been accessed the more likely that it is in the cache and so the file copy will be faster, the inverse is true for old timestamps. 

Sometimes when you have just opened a file and you then browse the location of that file in nautilus, the icon/list item/thumbnail for that file will appear before the other files in the directory, perhaps the two are related.

---

