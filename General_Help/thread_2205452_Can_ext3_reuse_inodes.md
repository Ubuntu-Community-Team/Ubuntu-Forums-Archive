---
title: "Can ext3 reuse inodes?"
date: 2014-02-13
forum: General Help
---

### Post by SchnappiJedi on 2014-02-13
Ext3 (default file system for Ubuntu) creates a set number of inodes during install. Can these inodes be reused when a file is deleted?

---

### Post by Bashing-om on 2014-02-13
schnappi2; Hi !

Short answer is yes, then the "inode" is available for the next file allocation.
You are correct in that there is a limited number of inodes. When all the inodes are used, the system can do not more until some files are deleted.

[INDENT][INDENT]many many little files
[INDENT][INDENT][INDENT]not a good ting
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by SchnappiJedi on 2014-02-14
Great! To clarify. Say inode #: 12047 is used. If the file associated with it is deleted inode #: 12047 can be reused. 

Correct? Just want to make sure I understand you correctly.

---

### Post by Bashing-om on 2014-02-14
schnappi2; Morning !

That is correct, the inode then becomes "unlinked" and thus becomes reusable.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by tgalati4 on 2014-02-14
Some reading:

[http://www.cyberciti.biz/faq/linux-show-contents-of-filesystem-superblock-inode/](http://www.cyberciti.biz/faq/linux-show-contents-of-filesystem-superblock-inode/)

[http://www.cyberciti.biz/faq/how-do-i-find-out-more-information-about-ext3-or-ext2-file-system/](http://www.cyberciti.biz/faq/how-do-i-find-out-more-information-about-ext3-or-ext2-file-system/)

[http://stackoverflow.com/questions/2062533/number-of-inodes-in-a-partition-not-matching-up-to-the-maximum-number-of-inodes](http://stackoverflow.com/questions/2062533/number-of-inodes-in-a-partition-not-matching-up-to-the-maximum-number-of-inodes)

[http://www.linuxquestions.org/questions/linux-newbie-8/check-inode-table-694242/](http://www.linuxquestions.org/questions/linux-newbie-8/check-inode-table-694242/)

---

### Post by SchnappiJedi on 2014-02-22
Thanks.

---

### Post by Bashing-om on 2014-02-22
schnappi2; Hey ,

No problem;

we are all
[INDENT][INDENT]here to help
[/INDENT][/INDENT]

---

