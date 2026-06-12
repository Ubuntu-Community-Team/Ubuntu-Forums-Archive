---
title: "Unable to Mount the volume"
date: 2008-02-01
forum: General Help
---

### Post by Seto Kiaba on 2008-02-01
I had to reinstall Ubuntu a day ago, due to a network problem.  I am using a laptop with a dual boot between Ubuntu and Windows XP.  When I installed it, everything was working great, and I could access the partition Windows was on.  However, the next day, I couldn't access that partition from Ubuntu, and Windows will not load now.  Whenever I try mounting that partition, I get this error: 
> 
Cannot Mound the volume
Unable to mount the volume

$LogFile indicates unclean shutdown (0,1)  Falied to mount '/dev/sda2': Operation not supported Mount id denied because NTFS is marked to be in use

I don't even care that much about saving Windows at this point, I just need access to that partition so I can save whatever files that are on there.  Is there a way to access the partition?

---

### Post by logos34 on 2008-02-01
You have to find a way to boot into it (even if only in safe mode) in order to shut it down properly.  Try running **chkdsk /r** from the recovery console on the XP install CD.  Then see if you can boot into it.

---

