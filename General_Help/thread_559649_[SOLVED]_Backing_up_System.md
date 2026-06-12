---
title: "[SOLVED] Backing up System"
date: 2007-09-25
forum: General Help
---

### Post by tech9 on 2007-09-25
When I run this command....

tar cvpzf backup.tgz --exclude=/ect/fstab --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

I want to exclude /ect/fstab, but when I extract the tgz file, I see fstab under /ect...

The reason that I want to back up the entire system and exclude the fstab file, is so I will be able to restore all data, in the event of deleting and creating new partitions.

Any ideas?

---

### Post by kebes on 2007-09-25
> **tech9 said:**
> When I run this command....

tar cvpzf backup.tgz --exclude=/ect/fstab --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

I want to exclude /ect/fstab, but when I extract the tgz file, I see fstab under /ect...

The reason that I want to back up the entire system and exclude the fstab file, is so I will be able to restore all data, in the event of deleting and creating new partitions.

Any ideas?

In your post, you wrote "--exclude=/ect/fstab" but presumably you meant "--exclude=/**etc**/fstab", right? Did you perhaps make that typo in your backup script?

---

### Post by kebes on 2007-09-25
Another idea... perhaps you could try enumerating the files/directories to exclude in a text file, and then use tar's "--exclude-from" option to specify that exclusion file.

Of course, it shouldn't make any difference... but maybe that will work better.

---

### Post by tech9 on 2007-09-25
> **kebes said:**
> In your post, you wrote "--exclude=/ect/fstab" but presumably you meant "--exclude=/**etc**/fstab", right? Did you perhaps make that typo in your backup script?

you're right.. I can't believe I made a typo     ](*,)

Thanks Kebes!!!

---

### Post by tech9 on 2007-12-06
I have solved this issue....

[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)

---

