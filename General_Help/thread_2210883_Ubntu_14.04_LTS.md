---
title: "Ubntu 14.04 LTS"
date: 2014-03-13
forum: General Help
---

### Post by wegmarsno on 2014-03-13
Hi all,     I wonder if someone could kindly answer the following 2 questions;

1)  Will 14.04 LTS be " maintained" for 5 years as is 12.04 LTS ?

2)  I am a user of 12.04 LTS.  If I install 14.04 LTS,as I use a separate root and home partition,can I safely leave my present home partition,without formatting it without any "ill" effects,formatting only the root partition on the new 14.04 LTS install ?

Thanks,for any response.

---

### Post by ajgreeny on 2014-03-13
1) Yes, it will have 5 years support.

2) You should be OK with the same /home partition, though the different versions of some applications may cause minor configuration problems when you first start the new version of the application.

---

### Post by 3rdalbum on 2014-03-13
Yes, in fact the main purpose of having a separate /home is so it is preserved during upgrades from one version to another (although it's not even needed for that purpose anymore - Ubuntu's installer can preserve the /home even when it's in the same partition as /)

Use the Upgrade option in the Ubuntu installer. If there's no Upgrade option, click on Something Else. Click on the partition that currently holds your / and tell Ubuntu to set its mountpoint to /.

Then click on your /home partition and tell Ubuntu to set its mount point to /home

Do not elect to format the /home partition, of course.

Continue with the installation and you're done.

---

### Post by wegmarsno on 2014-03-13
Thank you,  ajgreeny and 3rdalbum for answering my post so quickly and clearly.

---

