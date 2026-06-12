---
title: "looking for recovering files !!"
date: 2007-02-17
forum: General Help
---

### Post by Mba7eth on 2007-02-17
Hi all , I have mistakely deleted a file with rm command , search in the forum for hope to recover. But i have seen many people(including admins of this forum) telling that it is impossible, whereas others say it is  possible and they really recovered their files..... here are the links : 

[http://www.cgsecurity.org/wiki/PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")
[http://www.dtidata.com/recover_it_all_linux.htm]("http://www.dtidata.com/recover_it_all_linux.htm")
[http://foremost.sourceforge.net/]("http://foremost.sourceforge.net/")
[http://www.ubuntuforums.org/showthread.php?t=215952&highlight=recover+deleted+file]("http://www.ubuntuforums.org/showthread.php?t=215952&highlight=recover+deleted+file")
[http://jbj.rapanden.dk/magicrescue/]("http://jbj.rapanden.dk/magicrescue/")

and alot more


and remember this : 
> Q: How can I recover (undelete) deleted files from my ext3 partition?
Actually, you can't! This is what one of the developers, Andreas Dilger, said about it:

In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone.

Your only hope is to "grep" for parts of your files that have been deleted and hope for the best.


The question is for you :-$ guys , Ubuntu ultimate stuff and admins?  Can we recover files ?

---

### Post by nereid on 2007-02-17
Maybe you would like to take a look at this [linux.com](http://www.linux.com/article.pl?sid=06/10/30/1652211) article.

---

