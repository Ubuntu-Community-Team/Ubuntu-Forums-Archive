---
title: "Hard drive activity but random and short lived."
date: 2008-05-06
forum: General Help
---

### Post by funky_munky on 2008-05-06
Hi, I just installed Ubuntu Hardy Heron on my wifes computer after she finally gave up on Vista.  The laptop is a Lenovo 3000 N100 if it matters.  Anyway so far she likes it much better than Vista but I noticed something strange today.  After the computer is idle the harddrive knocks about once every 10-15 seconds but is not regular.  That is the average time.  If the disk is busy then it does not make any more noise than usual.  I am having a hard time finding out what process is causing it as it lasts only about 3/10ths of a second or so.  If anyone could help me track down what is causing this I would be much obliged.

---

### Post by bingoUV on 2008-05-06
Read [http://ubuntuforums.org/showpost.php?p=4834642&postcount=3](http://ubuntuforums.org/showpost.php?p=4834642&postcount=3) to find out the cause of disk access.   

Most likely it is the ext3 filesystem making journal entries.

---

