---
title: "undelete via ssh to OSX"
date: 2008-04-16
forum: General Help
---

### Post by Nopposan on 2008-04-16
Hello.  I have a rather odd problem.  Someone asked me if it's possible to recover a file from an OSX file system via my Linux box that's connected via SSH to that same OSX server.  I found some softwares called "foremost" and "magicrescue" that seem pretty nice for if I lost or deleted some files right here on my hard drive, but I don't know if I can run these softwares remotely, and I certainly don't know how.

Please inform me whether it's possible to do this, and if it is, then let me know how.  Oh, a software called "bacula" also looks like an interesting possibility.

Thank you.

---

### Post by kidders on 2008-04-17
Hi there,

I don't know much about magicrescue, but foremost needs direct access to the raw filesystem data ... something you may have trouble getting hold of remotely. I would suggest...
[LIST]
[*]running foremost on the Mac, or
[*]dumping the contents of /dev/disk0s2 (or whatever you want to recover data from) to a file, copying it to your Linux box, and running foremost on that instead.
[/LIST]

There are also plenty of file recovery apps available for OSX ... but if you're looking for a way to run a recovery operation using only SSH and your Linux box, dumping the Mac's filesystem to a file is your best bet. Once you're done, you could access it directly (over NFS or SFTP), if you don't want to copy it.

---

### Post by Nopposan on 2008-04-22
Thank you, Kidders.  I'll remember that.

---

