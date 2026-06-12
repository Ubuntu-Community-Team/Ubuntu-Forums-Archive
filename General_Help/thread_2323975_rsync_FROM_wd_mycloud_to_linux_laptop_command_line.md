---
title: "rsync FROM wd mycloud to linux laptop command line"
date: 2016-05-09
forum: General Help
---

### Post by roland-logikalsolutions on 2016-05-09
All,

this should be simple, but the answer is not obvious from searches. I can easily bookmark mycloud folders with the GUI, but I'm looking for a solution which will let me rsync FROM a directory tree on mycloud TO my laptop. That way when files are copied or changed via other systems I can quickly sync. I've found many instructions with hacks to do permanent mounts, but it "should" be possible to create a shell script which can do this on demand without having to permanent mount.

Any suggestions?

---

### Post by nerdtron on 2016-05-09
rsync relies on ssh connection to login on the remote server and then copy the files/folders you've specified.

Basically the syntax is like this:
```
 rsync -avrh --progress user@IP.address.server:/source/folder/here /local/destination/folder/here 
```

-a means to archive or preserve modification time
-r means recursive to copy folders and sub folder contents
-v for verbosity only
-h for human readable output
--progress to see the progress of the copying

You did not provide any details on you mycloud on how you login (is ssh even possible?) and how you copy the files so that's all I can help for now.
You can also upload via rysnc by interchanging the source and destination.

---

