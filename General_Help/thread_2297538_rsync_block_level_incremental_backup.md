---
title: "rsync block level incremental backup"
date: 2015-10-04
forum: General Help
---

### Post by speedojoe2 on 2015-10-04
[FONT=verdana]I'm trying to test rsync's block level backup functionality, but the time taken doesn't seem to decrease when I transfer a modified version of the large randomly generated file I'm working with. Any help would be appreciated.[/FONT]
[FONT=verdana]
These are the test files. rand2.txt is based on rand1.txt with the first character from each line removed.[/FONT]
```

-rw-rw-r-- 1 local local 954M Oct  4 17:59 rand1.txt
-rw-rw-r-- 1 local local 942M Oct  4 20:29 rand2.txt

```

[FONT=verdana]Initial transfer command and console output.[/FONT]
```

rsync -avhP --log-file=1st.txt /data/rsynctest/src/rand1.txt 192.168.0.5:/home/local/Desktop/dst/rand.txt

sending incremental file list
rand1.txt
          1.00G 100%   73.25MB/s    0:00:13 (xfr#1, to-chk=0/1)
sent 1.00G bytes  received 35 bytes  57.16M bytes/sec
total size is 1.00G  speedup is 1.00

```

[FONT=verdana]  Second transfer command and console output.[/FONT]
```

rsync -avhP --log-file=2nd.txt /data/rsynctest/src/rand2.txt 192.168.0.5:/home/local/Desktop/dst/rand.txt

sending incremental file list
rand2.txt
        987.01M 100%   26.77MB/s    0:00:35 (xfr#1, to-chk=0/1)
sent 987.25M bytes  received 221.46K bytes  23.23M bytes/sec
total size is 987.01M  speedup is 1.00

```

[FONT=verdana]Logs.[/FONT]
```

::::::::::::::
1st.txt
::::::::::::::
2015/10/04 22:10:22 [19691] building file list
2015/10/04 22:10:35 [19691] <f+++++++++ rand1.txt
2015/10/04 22:10:35 [19691] sent 1.00G bytes  received 35 bytes  57.16M bytes/sec
2015/10/04 22:10:35 [19691] total size is 1.00G  speedup is 1.00
::::::::::::::
2nd.txt
::::::::::::::
2015/10/04 22:11:02 [19696] building file list
2015/10/04 22:11:39 [19696] <f.st...... rand2.txt
2015/10/04 22:11:40 [19696] sent 987.25M bytes  received 221.46K bytes  23.23M bytes/sec
2015/10/04 22:11:40 [19696] total size is 987.01M  speedup is 1.00

```[FONT=verdana]

 Just tried with matching source and destination file names, which made no difference.[/FONT]
[FONT=verdana]
I'm confused as to why the second transfer takes longer than the first. Shouldn't block level kick in, recognise the second transfer is smaller by 12M and complete almost instantly?[/FONT]
[FONT=verdana]Does this only work when the second transfer is larger than the first? Is the difference between the two files not significant enough, therefore confusingly transferring the whole file? Or is it in fact working and my test isn't good enough?[/FONT]

---

### Post by TheFu on 2015-10-05
The more blocks there are, the more comparisons are needed. That means the disk performance on both systems AND the CPU on both matters greatly. I found that trying to sync files with small changes that were over 1G in size just didn't work well.  In my situation, those files were virtual machine virtual-HDDs and the purpose was system backups.  I switched to treating each VM just like a physical machine and doing backups from inside the VMs, which is usually lots of relatively small files. rdiff-backup of my tool of choice - system backups normally require about 2-3 minutes for 20G VMs, whereas with rsync the backups were 45+ minutes.

Also, if the rsync is happening on a single machine, the defaults don't do any comparisons - the file is just copied over. Of course, check the very extensive rsync manpage for the exact details.

You might find this [http://blog.jdpfu.com/2010/10/27/file-copy-performance-for-large-files](http://blog.jdpfu.com/2010/10/27/file-copy-performance-for-large-files) interesting. I found rsync to be the slowest method when dealing with large files.  bigsync and zsync may be better options if there are just a few files.

---

