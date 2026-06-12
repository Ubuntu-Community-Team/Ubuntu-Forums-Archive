---
title: "filesystem or hardisk failure"
date: 2007-03-29
forum: General Help
---

### Post by marco87otk on 2007-03-29
Dear All,

I have an external hard drive that is failing to work. I receive IO Buffer Errors while trying to access to some specific data. This turns into, as the first consequence, that the hard drive becomes read only. Now, The hdd is still in warranty and hence i would like to return it (if it will turn out to be broken). Still I would like to understand if the problem is related to something like a failure of the filesystem or to the fact that the harddrive might be broken. I say so since, with extremely lot of luck, i recently had also my laptop hardrive that gave me the same errors and those were due to the fact that it was consumed/broeken till its mechanical bonds (3 years of 24/24 work). 

So how can i check if the problem is correctable or not? maybe from the type of errors that fsck returns me? without of course reformatting and checking if they are still there?

The hard drive is in ext3, 300 GB.

Thank you very much for your help,
Really appreciating, 
marco

---

### Post by acormack on 2007-03-30
Marco

Does the disk device appear in LINUX at all?  

Have you tried unmounting the disk and running sudo fsck {device}  ?

If so what output dows fsck return?

Alec

---

### Post by Ocxic on 2007-03-30
I've had this exact thing happen to mee, you could do a zero fill to the drive, that would fix it temporarily, but everytime you restart your computer, you run the risk of it happening again, however for me this was only confined to a certain part of the disk, and i could partition around it, but it's a sure sign my drive was failing, now I can't even use it

---

### Post by marco87otk on 2007-03-30
Thanks Ocxic,

This is actually what I though and hence I will seriously think to return the drive...

@acormack, of course it does, of course i did, and.. IO Buffer Errorsm :)

thanks!

---

