---
title: "rsync understanding - total, received, sent"
date: 2016-01-11
forum: General Help
---

### Post by Drenriza on 2016-01-11
Edited post, please see #2

Hi all

I have setup a backup system with incremental backups
You can see here [http://ubuntuforums.org/showthread.php?t=2286156](http://ubuntuforums.org/showthread.php?t=2286156)

My questions are
[LIST]
[*]How many bytes does each incremental backup take. 
[*]How many bytes does the entire backup take. Incremental + linked files for incremental backup
[LIST]
[*]Same as above just for full backups 
[/LIST]
  
[*]How many bytes was sent from the sending side to the receiving side.
[LIST]
[*]How many bytes was send the opposite direction 
[/LIST]
  
[/LIST]
The reason i would like to know the above is that i would like to be able to make the following
[LIST]
[*]A graph that shows my expected storage needs based on my backups. 
[*]A graph that shows my BW consumption (bytes). 
[/LIST]

---

### Post by Drenriza on 2016-01-12
_It dosent make sense._

My rsync commands

Full backup
```
rsync -v -e "ssh -t -v" -a --itemize-changes --stats --recursive --compress --rsync-path="sudo mkdir /path.full.dir && sudo rsync" --remote-option=--log-file=/path/${DATE}.full.dir/rsync.log --files-from=/path/include.cfg --exclude-from=/path/exclude.cfg / ${BACKUPSERVER}:/path/${DATE}.full.dir 1> /path/rsync.local.log 2>&1
```

Incremental backup
```
rsync -v -e "ssh -t -v" -a --itemize-changes --stats --recursive --compress --rsync-path="sudo mkdir /path.inc.dir && sudo rsync" --remote-option=--log-file=/path/${DATE}.inc.dir/rsync.log --link-dest=/path/${RLINKDEST} --files-from=/path/include.cfg --exclude-from=/path/exclude.cfg / ${BACKUPSERVER}:/path/${DATE}.inc.dir 1> /path/rsync.local.log 2>&1
```

When i run rsync i create both a local and remote log file.
The difference between the two is that the local one also show --stats while the remote log file exclude this.

**_Information and question_**
The sending side - incremental backup
> 
**--stats output**
Number of files: 434,652 (reg: 360,823, dir: 72,773, link: 1,056)
Number of created files: 273 (reg: 233, dir: 40)
Number of deleted files: 0
Number of regular files transferred: 277
Total file size: 232,465,609,686 bytes
Total transferred file size: 4,839,950,530 bytes
Literal data: 4,746,455,971 bytes
Matched data: 93,494,559 bytes
File list size: 3,209,843
File list generation time: 0.028 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 4,741,953,365
Total bytes received: 202,888

sent 4,741,953,365 bytes  received 202,888 bytes  10,456,794.38 bytes/sec
total size is 232,465,609,686  speedup is 49.02

[LIST]
[*]Total transferred file size equals literal data + matched data.
[LIST]
[*]
[LIST]
[*][I]Literal data - is how much unmatched file-update data we had to send to the receiver for it to recreate the updated files.
[/I]
[*]*Matched data - is how much data the receiver got locally when recreating the updated files.*
[LIST]
[*]Meaning that the file list amount rsync needed to get locally was 93.494.559 bytes. And this data take up 227.625.659.156 bytes? Total file size minus total transferred file size.
[/LIST]
[/LIST]

[*]*Total transferred file size is the total sum of all files sizes for just the transferred files*
[LIST]
[*]So this is the bytes of the incremental backup from the full backup on the receiving side? Aka this is the size of the entire incremental backup?
[/LIST]
[/LIST]
[/LIST]

The above is fuzzy but this is what i DON'T GET AT ALL

The receiving side - incremental backup
> 
**--remote-option=--log-file=/path/**
sent 202,893 bytes  received 4,741,953,373 bytes  total size 232,465,609,686


**Different send and receive byte amount**
The bytes sent and received from the sending and receiving size differs in bytes, why?
Does rsync calculate TCP windowing and ACK's? So if the sending side send 100 packages with ACK 100 and receive a ACK 90 this is calculated into send and receive?
But that also dosent make sense since the sending has send less bytes than the receiving side has received??????

Also the literal data (bytes) amount is greather than the sending side has sent?

Pretty much the only thing the two sides agree on are the total file size of 232.465.609.686 bytes.
But
```
du -csb /backup/file exclude=[the remote log file]
```
adds up to 232.771.683.286 bytes
```
du -csb /backup/file
```
adds up to 232.771.729.034
Neither adds up to what rsync says the backup takes up in bytes.......

I am definitely thinking i am missing something, but i would REALLY like to know what [ mind..... blown ]

---

### Post by Drenriza on 2016-01-18
No one at all?

---

### Post by mastablasta on 2016-01-18
> **Drenriza said:**
> 
My questions are
[LIST]
[*]How many bytes does each incremental backup take.
[*]How many bytes does the entire backup take. Incremental + linked files for incremental backup
[LIST]
[*]Same as above just for full backups
[/LIST]
[/LIST]


Depends how many changes you made to the file and how often you backup. also depends on how much a file can be compressed and such. e.g. jpeg pics are already compressed and can't be compressed much anymore. text is another matter. 

> 

[LIST]
[*]How many bytes was sent from the sending side to the receiving side.
[LIST]
[*]How many bytes was send the opposite direction
[/LIST]
[/LIST]
The reason i would like to know the above is that i would like to be able to make the following
[LIST]
[*]A graph that shows my expected storage needs based on my backups.
[*]A graph that shows my BW consumption (bytes).

Someone else might help you better. but you need about 50% more disk space than files you backup. I would say about 30% added space for increments (depends how often you do it and how long and how many version do you keep). then about 10-20 % (again depends on disk size) should be left empty so that disk can run well. a fully filled disk in ext4 is not good. nearly full disk will slow down read&write considerably. someone with more experience might be able to correct my numbers. :-p
[/LIST]

in any case you should know there are static files (that do not change often and you backup-e.g. photos) and there might be dynamic files that change very often. the dynamic ones will have many versions, while the static files will basically have only one.

---

### Post by Drenriza on 2016-02-23
Thanks for the reply mastablasta!!

I already got all the information i need through rsync and its logging features. But i dont understand the numbers rsync gives me since the sending side got one set of numbers that dosent match up to what the receiving side says it received and sent.
Also the two docent agree on the total file size (all the files in bytes combined). Which makes me wonder how one is suppose to read these information.

And i am hoping someone can help me figure that out

---

