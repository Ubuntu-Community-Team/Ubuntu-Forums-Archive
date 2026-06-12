---
title: "How to get rid of incorrect back-ups ?"
date: 2023-10-10
forum: General Help
---

### Post by mathieud on 2023-10-10
Hello,

I use Déjà Dup to back-up my computer to a USB drive.

Unfortunately, the drive failed during or shortly after the last back-up which was a full back-up. I bought a new disk and moved the back-up files there. From this, Déjà Dup was able to run an incremental back-up.

However, I'm almost sure that some files belonging to the full back-up where not copied correctly (because of the failure). Therefore, the I'm almost sure that the full back-up (and therefore the incremental one) is incorrect.

Is it possible to remove this full back-up (and the incremental one) ? This would be the best solution I think. Otherwise, is it possible force a new full back-up (with Déjà Dup) ?

I did my best to try to remove the backup (even with duplicity CLI) but couldn't find a way.

Thanks in advance,
Mathieu

---

### Post by Tadaen_Sylvermane on 2023-10-10
It won't affect anything. It may have a partial file or something but it won't hurt the majority of the back up. If you have it set to automatically remove backups older than X date it will remove it when it gets to that time.

If it bothers you that much, if you are sure you have all the data on your machine there is also no harm in pointing to a different location and running a totally new backup again. Don't delete the old one just start a new one. That way you can hang onto the old one for however long you think you may need it.

---

### Post by #&amp;thj^% on 2023-10-10
I'm not a fan of Duplicity, but this may help:
```
cleanup --extra-clean --force
```
It can be a bit confusing as the Duplicity documentation makes out that this command will remove all backups except for the last 2 full backups.
ie:
```
remove-all-but-n-full 2 
```
And you found out it won't.
And i agree with Tadaen_Sylvermane:
> If it bothers you that much, if you are sure you have all the data on your machine there is also no harm in pointing to a different location and running a totally new backup again. Don't delete the old one just start a new one. That way you can hang onto the old one for however long you think you may need it. 

---

