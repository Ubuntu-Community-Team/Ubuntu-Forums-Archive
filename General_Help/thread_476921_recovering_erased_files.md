---
title: "recovering erased files"
date: 2007-06-17
forum: General Help
---

### Post by Ralph Boland on 2007-06-17
I just erased all the work I did today (by my favorite method: tar cvf list of files to tar).
Is there a way to recover my lost file (It a days work).
If not how do I recover my work as of the end of yesterday?

I am on Ununtu 6.10.

Ralph Boland

---

### Post by atlfalcons866 on 2007-06-17
if its ext3 you cant 

From [http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html](http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html)
Q: How can I recover (undelete) deleted files from my ext3 partition?
Actually, you can't! This is what one of the developers, Andreas Dilger, said about it:

In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone.

Your only hope is to "grep" for parts of your files that have been deleted and hope for the best.

---

### Post by rob.webinator on 2007-07-18
Curiously, how does one ""grep" for parts of your files that have been deleted and hope for the best."?  

I, I mean a friend just deleted one of my (I mean his) files that haven't been backed up yet.  It was a text file and just having fragments of it would be nice.

---

### Post by az on 2007-07-18
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Use foremost or sleuthkit.

---

### Post by bodhi.zazen on 2007-07-18
[https://answers.launchpad.net/ubuntu/+question/2178](https://answers.launchpad.net/ubuntu/+question/2178)

---

