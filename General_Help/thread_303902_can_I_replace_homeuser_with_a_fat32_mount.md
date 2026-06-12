---
title: "can I replace /home/user with a fat32 mount?"
date: 2006-11-21
forum: General Help
---

### Post by rossgemuend on 2006-11-21
I would like to expand the space available to my /home/usr_name directory without repartitioning and I'm wondering if I can mount my 40gb fat32 partition and have it replace my user folder. Is this possible?

---

### Post by aysiu on 2006-11-21
I wouldn't advise using FAT32 for a Linux filesystem.

---

### Post by orb9220 on 2006-11-21
Sorry you can't use fat32 for linux. For all my music,movies,pics,ect I have a 112GB fat32 that I mount so xp and ubuntu can read and write to.

There are threads here to move your home from one ext3 partition to another.
and editing your fstab to point to new home.

---

### Post by CatKiller on 2006-11-21
As everyone else has said, you don't want to mount your FAT32 partition **as** your home folder. It's far too broken for that. You can, however, mount it **in** your home folder if it's already got stuff on that you want to keep. As /home/rossgemuend/documents, say. Then you can put some of your static data things in there and relieve the partition that contains the rest of your filesystem.

If there's nothing on there that you want to keep, format it up as the more sensible ext3 and use it as you wish. aysiu has a [howto]("http://www.psychocats.net/ubuntu/separatehome") detailing how to do so. To reiterate, **don't** use FAT32 for this - or NTFS for that matter. It will all go hideously wrong.

---

