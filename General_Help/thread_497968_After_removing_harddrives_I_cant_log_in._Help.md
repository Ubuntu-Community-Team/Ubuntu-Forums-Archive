---
title: "After removing harddrives I cant log in. Help"
date: 2007-07-10
forum: General Help
---

### Post by Christof999 on 2007-07-10
Hello,

I recently removed 2 SATA hard drives from my computer to put in a NAS. I currently have two left in my Computer. One for the OS and one for storage. Since I removed the two Hard drives my system will boot up, but I cant get into the desktop. It gives me a permissions error. I think I know the problem, since the drives were changed around, the drives got new dev numbers. For example, my Boot drive used to be sdc1 nows its sda1 etc. How do I fix it, so that the system sees the root and home partition in the new dev number ?

I am able to get to a terminal to access the system and use the Live CD

Thanks
C.

---

### Post by thunderduck3141 on 2007-07-10
edit your fstab so that the changes can be recognized by Ubuntu
i forget where its located so just do 

whereis fstab

make sure ur root when u edit it

---

