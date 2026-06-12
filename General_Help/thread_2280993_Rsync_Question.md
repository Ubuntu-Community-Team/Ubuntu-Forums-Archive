---
title: "Rsync Question"
date: 2015-06-03
forum: General Help
---

### Post by GrouchyGaijin on 2015-06-03
I am trying to use rsync to sync files from one directory to another.
The thing is that I only want to sync files that match a specific pattern in the file name.
I set this pattern via:
```
 read -p "Enter the episode as mmddyy: " episode 
```
Prior to attempting to use rsync I was using a simple mv command.
```
 mv "$episode"*.mp3 /destination/directory 
```

My question is, can someone explain how I can limit the files synced to  files that contain the $episode variable using rsync?
I've tried various ways of writing the command, but end up with every file in the source directory being copied to the destination directory.

---

### Post by Keith_Helms on 2015-06-03
It works for me.   I set a variable containing part of the filename, then used an rsync command using that variable along with wildcards in dry run mode and it only listed the files I wanted:
```
keith@sager-laptop:/homedata/Podcasts/Science Friday Audio Podcast$ TESTVAR=201505
keith@sager-laptop:/homedata/Podcasts/Science Friday Audio Podcast$ rsync -van sci*$TESTVAR*.mp3 /data2/testrsync
sending incremental file list
scifri201505011p.mp3
scifri201505012p.mp3
scifri201505081p.mp3
scifri201505082p.mp3
scifri201505151p.mp3
scifri201505152p.mp3
scifri201505221p.mp3
scifri201505222p.mp3
scifri201505291p.mp3
scifri201505292p.mp3

sent 321 bytes  received 46 bytes  734.00 bytes/sec
total size is 447,935,452  speedup is 1,220,532.57 (DRY RUN)

```

---

### Post by GrouchyGaijin on 2015-06-03
Cool - let me try it again

---

### Post by GrouchyGaijin on 2015-06-03
Thanks man,

It works for me now as well.  I guess I was just writing the command incorrectly.

---

