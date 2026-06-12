---
title: "Folder permissions"
date: 2007-04-09
forum: General Help
---

### Post by vishnumrao on 2007-04-09
Hi all,

I installed fiesty beta over the weekend replacing FC6. I had a home directory in FC (110GB, ext3). I have a lot of stuff in there.  After installing Feisty, the drive shows up as /media/hda2. But I notice all those files in the partition are locked. 

I tried chmod 777 /media/foldername/ foldername. does not work. It changes permisson to the folder but all the files inside are locked. 

How can I remove the lock on all files in the partition. i.e  how to give full access to the user (there is only one user). 


Thanks in advance,
Vishnu Rao.

---

### Post by aysiu on 2007-04-10
```
sudo chown -R vishnumrao:vishnumrao /media/hda2
``` From *man chown*: > OPTIONS

 -R      Change the user ID and/or the group ID for the file hierarchies
             rooted in the files instead of just the files themselves.

---

### Post by maheshjagadeesan on 2007-04-10
As an alternative to aysiu's solution, you could also try adding a umask to the partition in question in /etc/fstab. I had the same problem, and I resolved it somehow, don't exactly remember....

---

### Post by vishnumrao on 2007-04-10
Thanks for your suggestions. I already tried out Aysiu's advice. Works. 

One more question. The partition I mentioned above was my home partition in Fedora. I would like to make this my home directory. Any ideas? 

Thanks once again,
Vishnu Rao.

---

### Post by aysiu on 2007-04-10
I wouldn't advise it. Conventional wisdom says that sharing a /home partition between different Linux distros can lead to weird problems or light breakage.

Your best bet is to copy over the config files that are important to you (for me, that's ~/.mozilla and ~/.thunderbird) and then just leave it as a "documents" partition to store files (pictures, music, videos, documents, etc.).

---

