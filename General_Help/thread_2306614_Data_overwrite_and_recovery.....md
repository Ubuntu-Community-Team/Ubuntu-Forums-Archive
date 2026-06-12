---
title: "Data overwrite and recovery...."
date: 2015-12-17
forum: General Help
---

### Post by Motuka on 2015-12-17
I know such related questions have been answered over and over, but please bear up with me.....
I have a memory stick. I want to overwrite everything on it but still cannot make it! I started with bleachbit, but the results did not work. I did a **sudo dd if=/dev/urandom of=/media/USER/DRIVE/dummy_file **until it was full, then I did a **sudo shred -zvfu -n 3 /media/USER/DRIVE/dummy_file** to overwrite and remove, then it still does not seem to overwrite the data. I recovered the files to the /media/USER/DRIVE and again did a shred of every single recovered file.. Then they were there! 
Can somebody help me how to overwrite a flash drive/memory stick? Am I missing any information, kindly help me point it out.

NB: The recovery tool I use is photorec from testdisk.

---

### Post by sudodus on 2015-12-17
You can try with mkusb

[mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

In your case I suggest that you select 

**w "wipe the Whole device - consider other options except for special cases" **

and consider that this is a special case.

---

