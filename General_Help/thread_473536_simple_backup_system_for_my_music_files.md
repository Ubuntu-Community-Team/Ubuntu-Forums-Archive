---
title: "simple backup system for my music files?"
date: 2007-06-14
forum: General Help
---

### Post by Vincent Plagnol on 2007-06-14
Hello all,

I am looking to backup my music on a portable hard drive. It's roughly 30Gb and I want something incremental, that only copies the files that have changed and not the entire folder each time I do a backup. I don't want to compress it either, the hard drive is large enough to handle the entire music folder.

I'd like something simple really, it seems like an easy task but all the softwares I have found seem to be much more powerful than what I need.

Any recommendations? 

Thanks in advance,

Vincent

---

### Post by vanadium on 2007-06-14
I am doing this:

```

rsync -av --del /media/MEDIA/Music/ /home/vanadium/mnt/backup/Music/

```

This is using rsync. It will only copy the differences between source (/media/MEDIA/Music in my case, that is a Lacie portable USB) and destination (located in my case on a desktop mounted over the network using nfs).

the --del switch will delete files on the destination that do not exist (anymore) on the source.

For your ease (and prevent typing mistakes), you should put this command into a bash script in your path. You can then simply type the name of the bash script to perform the backup.

---

### Post by crane on 2007-06-14
You could also add the script to a cron job and let it run automaticly. One warning with the delete option. If you ever decide you should want to have some music on your server but not you player this could cause a problem. If you delete it from you player then run the script it will remove your back-up as well.

But rsync should do the job for you.

---

### Post by vanadium on 2007-06-14
Indeed, a warning is in place with the --del switch. If you mistakenly give an empty directory as source, your destination will be wiped out (= sychronised with the source disk). For this reason, you better omit the --del the first time you try the command.

---

### Post by Vincent Plagnol on 2007-06-14
Thanks guys, it worked beautifully, exactly what I wanted. 
For the record it took me a bit of time to understand how to exclude some files (I wanted to back up my music but not the TV shows...), so I attach the line of code that did the job for me:


```

rsync -av --del --exclude=iTunes\ Music/TV\ Shows/*  /media/windows/Users/vplagnol/Music/iTunes/iTunes\ Music /media/HANDY080/music_backup/

```

---

