---
title: "Top backup software?"
date: 2007-11-30
forum: General Help
---

### Post by JaggedOne on 2007-11-30
I am curious what people suggest for backup software in linux. I just switched over from windows and know nothing about linux backups. There are two features I am looking for:
1. I want to be able to completely restore my entire system to a previous point, not just save important files.
2. The software should only need to pick up blocks that have changed after the first back up to save space.

---

### Post by navaburo on 2007-12-01
I just keep backups on an external hard disk. I don't plan on my system dying any time soon.

---

### Post by JaggedOne on 2007-12-01
Of course i will keep it on an external drive. Im looking for software to use to take the backup.

---

### Post by mahousaru on 2007-12-01
I use sbackup which you can easily install from Synaptic. You can set it manual or automatic, it will do a full backup initially and then do incrementals. 

This one is based on tar and gzip I guess it has its own code to work out what has been backed up or not.  There are others that are based on the don daddy of file syncing aka rsync, I tried several of them and they have their advantages and disadvantages compared to sbackup.  For example one I tried does a duplicate of your files so you don't need to wait for you eyebrows to regrow to grab the file.  But since is a mirror of your files you don't save space.  sbackup will compress so that is why I like it, but I suffer during recovery time.

The only thing missing from sbackup is a dialogue and cancel button which they are working on.

---

### Post by ntu on 2007-12-07
> For example one I tried does a duplicate of your files so you don't need to wait for you eyebrows to regrow to grab the file. But since is a mirror of your files you don't save space.

Mahousaru, would you give the name of this program please?

---

### Post by mmichalik on 2007-12-07
we use Bacula, which is in the repository as well and, it works good.  Does all of the things  you want to do to but, it can be a bit cumbersome to set up.

---

### Post by dimbulb1024 on 2007-12-07
> **mahousaru said:**
> I use sbackup which you can easily install from Synaptic. You can set it manual or automatic, it will do a full backup initially and then do incrementals. 

It has worked well for me very well.

---

### Post by mahousaru on 2007-12-07
> **ntu said:**
> Mahousaru, would you give the name of this program please?

I tested about 5 or 6 programs quite a while ago, (one was bacula) and I stupidly didn't keep notes of what I was doing *bonks head*

Some of them had really non backup sounding names and I had to install a few from their website.

Ok after having a coffee I would say that they were

flyback
rdiff
rsnapshot
sbackup
bacula
*im sure there was another one*

sorry I'm not much help :(

---

