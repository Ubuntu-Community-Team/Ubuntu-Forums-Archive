---
title: "rsync for data backup, safe or not"
date: 2015-02-21
forum: General Help
---

### Post by liruiradiant on 2015-02-21
Hi everyone,

I have some very important scientific data on a server, they are quite big(8TB), so I can only back it up once, rather than making multiple snapshots daily weekly and monthly.

I'm doing this by using: rsync    -avhH   --delete    /data      /backup
I run rsync with crontab everyday at 2:00 am.

Because the server disk is under heavy usage everyday. I'm worried it may get some bad sectors someday.

Suppose file-x get corrupted by bad sectors on day1 and becomes file-x'. I discovered it one month later at 9:00 am when I use this file. I didn't make any change to this file during the month. I started restoring the file from /backup/ folder immediately.

By default, rsync do 'quick check' on the file size and modification date.
file-x is on a bad sector and corrupted. But I didn't change the modification date and file size on purpose.
Will rsync detect the difference and copy the corrupted file-x' and replace the original file-x on the /backup/ folder? (Because of the corruption, the file size may change)
Or will rsync ignore the bad sector because file size and modification date didn't change and I can restore the intact file from /backup/?
Or will rsync detect the bad sector and abort the task with err messages on 2:00 am on day2?

Thanks a lot for some answers or other backup suggestions!

---

### Post by nerdtron on 2015-02-21
My rsync backup looks like this:

```
rsync -avvrhu --log-file=logs.txt  --delete --partial /source /backup
```

-a is important to preserve modification time, permission etc of the source files.
-u is important since it will only look for new files, it won't recopy the old files that haven't changed

Aside from that I think the best way to have your data safe is to have two backups copies on different hard drives. Or better yet, setup a backup server (with RAID) that will hold your data for the long run.

---

### Post by HermanAB on 2015-02-21
Howdy,

Rsync will safely copy data, that is all.  Data sitting on a disk is subject to bit rot - this is especially problematic with large archives.  Zfs and Btrfs (under development) provide protection but other file systems do not.

There are utilities that can be used to add parity bits so that corrupted archives can be repaired later, for example par2 and rsbep, described here:
[http://www.aeronetworks.ca/2013/12/nsa-and-error-proofing-your-archives.html](http://www.aeronetworks.ca/2013/12/nsa-and-error-proofing-your-archives.html)

---

### Post by buzzingrobot on 2015-02-21
rsync has been the dominant file synching tool in Unix/Linux for years.  You will find that most of the GUI backup tools are wrappers that gather info from a user and build and schedule can rsync job.

It offers a very long list of options and reasonably complex set of options.  

Set up a smaller-scale test environment to make sure your rsync job is safely and correctly doing what you want it to do before you turn it lose on that data.


*However*, rsync is intended for repeated and regular synchronizing of data sets. Since this is a one-time-only backup -- you don't plan on synching 8tb of data -- other, potentially simpler, options at might be worth looking. You're right to consider restoration, something many folks don't think about.

---

### Post by kjohri on 2015-02-25
There are two issues here, backup and the possibility of disk sectors going bad. rsync is excellent for backup. Regarding disk sectors, I think some lower level disk diagnostic programs should be of help like fsck. Or, you can use [RAID]("http://en.wikipedia.org/wiki/RAID").

---

