---
title: "Backup error"
date: 2016-07-11
forum: General Help
---

### Post by 4kh3RAm on 2016-07-11
I would to use backup but it gives this error.

> Permission denied when trying to create 'duplicity-full.2016.....difftar.gz

Any workaround ?

---

### Post by ian-weisser on 2016-07-11
Perhaps we need a bit more detail.

---

### Post by 4kh3RAm on 2016-07-12
Like what ?

I posted the error message.

I ran Backup located in Accessories.

---

### Post by deadflowr on 2016-07-12
Permission denied usually means you are trying to do something somewhere that is not allowable.
Like write the backup to a location not writable by the user.
So information about how and/or where to you are backing up, beyond the simple error message, would be helpful.

Something to look at is the ownership and permissions of both places used for the backup, the source and the destination.

Of course, that is not the only way or reason you would get that error.
But without a more thorough understanding of the situation, we can only guess.

Hope that helps

---

### Post by 4kh3RAm on 2016-07-12
Thanks for the details.

I got it to work by running as administrator.

However, I wanted to do an image backup.

I installed clonezilla to a CD.

And made a full disk backup.

---

