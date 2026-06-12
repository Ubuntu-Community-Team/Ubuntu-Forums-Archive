---
title: "can't rename files or folders"
date: 2008-06-21
forum: General Help
---

### Post by raylistic87 on 2008-06-21
Hi, I cant figure out why i cant rename my files suddenly. I can create them on desktop, but when i try to rename them, I cant type anything to change them. I have check the permission tab, it shows i can create and delete files and the files access it shows " -- ". Does anyone has any idea? Almost all my files and folders under Home has this issue.

Thanks.

-Ray

---

### Post by lost09 on 2008-06-21
A "-" means you do not have the corresponding permissions. It sounds as if your file permissions have somehow been altered. You may be interested in this tutorial on such things (I at least find it helpful): [http://linuxcommand.org/lts0070.php](http://linuxcommand.org/lts0070.php)

---

### Post by smo0th on 2008-06-21
try ```
sudo chmod 755 <file>
``` which will allow you to read, write and execute the file and all other users to read and execute, but not write.

---

