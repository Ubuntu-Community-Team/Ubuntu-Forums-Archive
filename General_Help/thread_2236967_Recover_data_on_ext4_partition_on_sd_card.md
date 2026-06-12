---
title: "Recover data on ext4 partition on sd card"
date: 2014-07-29
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2014-07-29
So I have a SD card that was running a in a rPi, i need to try to pull some data off it, every folder on the partition has vanished and the lost and found folder is packed with 26422 folders all starting with a # followed by 3 to 6 numbers
all i care about recovering is 2 or 3 small files that were in the /var/www folder

I have made a image file using ddrescue, i dont know what to do with it

EDIT:
I just dumped the output of the tree command to a text file and opened a 4.3MB file in a text editor and use ctrl+f to find my important fail based on the file name

---

### Post by tgalati4 on 2014-07-30
Install *testdisk* and run it.  It will try to rebuild the partition table and the file/directory structure.  If it can't, then run *photorec* (part of testdisk) to recover individual files.  If you know the exact file type that you are interested in, then just use *photorec* and recover *.html files for instance.

---

