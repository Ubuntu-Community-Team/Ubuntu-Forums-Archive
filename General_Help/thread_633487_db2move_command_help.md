---
title: "db2move command help"
date: 2007-12-06
forum: General Help
---

### Post by kstelzer on 2007-12-06
Hi Everyone, 

I have been doing some development using DB2 Express on Windows.  I would like to use db2move to migrate to ubuntu.  I have been using this document for guidance:

[http://www.ibm.com/developerworks/db2/library/techarticle/dm-0403melnyk](http://www.ibm.com/developerworks/db2/library/techarticle/dm-0403melnyk)

My problem is when I do a db2move dbname load I see this error:

Application code page not determined, using ANSI codepage 1208

Error opening report file. Terminating

Is this a db2 error in which I need to specify codepage before exporting out of windows or before trying to load into ubuntu.  Or is this a problem in ubuntu in which I need to 'download'  specific language codepages?

If anyone has ever encountered this problem or has solved it, I am open to any help/suggestions.  I have googled all day and nothing seems to work.  I am a newbie looking to switch to ubuntu, so be gentle.

Thanks

Kim

---

### Post by kstelzer on 2007-12-07
Well, through some more searching...I found a solution to this problem.  It was a read write file permission problem.  db2inst1 did not have permission to read and write the information from a file that was on my regular user account.  This is why it couldnt read the file, it wasn't that the codeset was wrong.

Kim

---

