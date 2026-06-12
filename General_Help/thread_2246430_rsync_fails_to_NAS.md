---
title: "rsync fails to NAS"
date: 2014-09-30
forum: General Help
---

### Post by barrytrujillo on 2014-09-30
*I'm trying to copy directories to a NAS on my local network with rsync.*

```
rsync -ah --progress /home/user/Movies/YoungFrankenstein/ /home/user/.gvfs/media\ on\ mediahub.local/videos/
```

sending incremental file list
./
rsync: failed to set permissions on "/home/user/.gvfs/media on mediahub.local/videos/.": Operation not supported (95)
Young.Frankenstein.1974.1080p.mp4
       1.71G 100%   48.53MB/s    0:00:33 (xfer#1, to-check=1/3)
moviecover.jpg
     130.68K 100%  178.23kB/s    0:00:00 (xfer#2, to-check=0/3)
rsync: mkstemp "/home/user/.gvfs/media on mediahub.local/videos/.Young.Frankenstein.1974.1080p.mp4.5uwv7r" failed: Operation not supported (95)
rsync: mkstemp "/home/user/.gvfs/media on mediahub.local/videos/.moviecover.jpg.K015en" failed: Operation not supported (95)

sent 1.71G bytes  received 53 bytes  49.67M bytes/sec
total size is 1.71G  speedup is 1.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]

*It shows the copy progress completes, but the files don't make it to the destination folder. I thought it might be a permissions issue on the NAS at first, but I don't have any trouble with creating new directories or copying files in Nautilus. Any help would be appreciated! Thanks!*

---

### Post by nerdtron on 2014-09-30
Problem with creation of temp files.
Have a look at this link: [http://www.jotschi.de/Uncategorized/2012/04/17/rsync-to-ftp-operation-not-supported-95.html](http://www.jotschi.de/Uncategorized/2012/04/17/rsync-to-ftp-operation-not-supported-95.html)

Or on this one: [http://www.linuxforums.org/forum/ubuntu-linux/140062-rsync-over-ftp-problem.html](http://www.linuxforums.org/forum/ubuntu-linux/140062-rsync-over-ftp-problem.html)

---

### Post by LewisTM on 2014-09-30
Hi there,
From the target path you specified, it seems you are copying to your NAS via SMB (Windows share). Most SMB servers wont support copying Linux properties like owner, group, permissions and modification time. That is implied in your -a switch (copy recursively retaining owner, group, time, perms and special files). Try rsync'ing without the a.
```
rsync --progress /home/user/Movies/YoungFrankenstein/ /home/user/.gvfs/media\ on\ mediahub.local/videos/
```
Cheers!

---

### Post by nerdtron on 2014-10-01
> **LewisTM said:**
> Hi there,
From the target path you specified, it seems you are copying to your NAS via SMB (Windows share). Most SMB servers wont support copying Linux properties like owner, group, permissions and modification time. That is implied in your -a switch (copy recursively retaining owner, group, time, perms and special files). Try rsync'ing without the a.
```
rsync --progress /home/user/Movies/YoungFrankenstein/ /home/user/.gvfs/media\ on\ mediahub.local/videos/
```
Cheers!

Even if you use the -a switch and file properties won't be copied, the files will still be copied and different error will be shown. If I remember the error should be " Some file properties were not copied" or something along those lines.
His error is rsync: mkstemp and the filename clearly have a 6 character extension. Clearly this is a problem on writing the temp files while transferring.

---

