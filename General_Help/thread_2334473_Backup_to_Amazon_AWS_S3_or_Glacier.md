---
title: "Backup to Amazon AWS S3 or Glacier"
date: 2016-08-19
forum: General Help
---

### Post by martin30002 on 2016-08-19
Anybody has experience in backups to amazon aws?
I see the following tools for accessing aws:
```

s3backer/xenial 1.4.2-1 amd64  
  Amazon AWS S3-backed virtual hard disk device

s3cmd/xenial,xenial 1.6.1-1 all
  command-line Amazon S3 client

s3fs/xenial 1.79+git90-g8f11507-2 amd64
  FUSE-based file system backed by Amazon S3

s3ql/xenial 2.15+dfsg-1 amd64
  Full-featured file system for online data storage

s3curl/xenial,xenial 1.0.0-1 all
  Easily interact with AWS S3 HTTP services

awscli/xenial,xenial 1.10.1-1 all
  Universal Command Line Environment for AWS

```

What tools are useful and how do they work?

---

### Post by Habitual on 2016-08-19
I've used both in the past.
s3cmd by far is the simplest, a command-line utility to "rsync-like" to s3:/buckets
that only needs maybe 2 edits to get running.

---

### Post by martin30002 on 2016-08-20
I'm just trying > aws s3 sync /home/me s3://name1/linux but it seems to scan all my hard disks and then it is very very slowly.
awscli is not usable.
But s3cmd seems to work ok.

---

### Post by martin30002 on 2016-08-23
Now I tested Deja-dup with backup to amazon S3. For this, you need the package python-boto.
But for AWS buckets in europe, there are bugs in the connection.py so it will not work very well.

---

### Post by Habitual on 2016-08-23
I forgot I have to relearn some new tools ('aws") to support the New Instance Length changes coming.
Grr. No Bid Deal.
Never tried "aws s3 sync" as I have "enough stuff" stored in far too many buckets. :(

Lots of Desktop client backup-to-S3 software out there also.
Even some native Linux programs can likely write to s3.

Writing big Files up there proved troublesome, so I went with rsync-like s3cmd.
How is "awscli is not usable"?

---

