---
title: "Using Amazon S3 like an external hard drive"
date: 2015-02-26
forum: General Help
---

### Post by Qu4rk on 2015-02-26
I'm looking for some advise on how to create my own cloud directory with Ubuntu.  So here is my scenario.

I have a desktop & a laptop.  I want to use Amazon S3 like an external hard drive.  I'm open to the method of how I do this.  I could be mounting, it could be syncing.

What I want to avoid:

S3fs has a limit of 5 GB per file.  I would like to avoid file size limits.
Also, I use my desktop 90% of the time.  I also want to avoid my laptop syncing & removing files because my sync system thinks I deleted it...but I just haven't used it in a while.

The functionality like dropbox would be great.

Any input would be great.

---

### Post by tgalati4 on 2015-02-26
There are a lot of libraries available to talk to Amazon AWS, but I'm not aware of a utility or program written to cover your Use Case:

```
apt-cache search amazon
```

I found a link setting up bittorrent in the Amazon cloud and using that to syncronize your files:  [http://samglover.net/bittorrent-sync-amazon-ec2/](http://samglover.net/bittorrent-sync-amazon-ec2/)

An alternative is to set up [http://owncloud.org](http://owncloud.org) on your own server and poke a hole in your firewall.

---

### Post by Qu4rk on 2015-02-26
Nice command.  I just found a program called S3QL using your search.  Does anyone here have much experience S3QL?  There is not much info on the web about it, outside of the devs page.

---

### Post by tgalati4 on 2015-02-26
I have not used it, but I have found some info:

[http://www.admin-magazine.com/HPC/Articles/HPC-Cloud-Storage](http://www.admin-magazine.com/HPC/Articles/HPC-Cloud-Storage)

[http://www.rath.org/s3ql-docs/mount.html](http://www.rath.org/s3ql-docs/mount.html)

Understand that cloud services have a tendency to float away.

---

### Post by dragonfly41 on 2015-02-27
There is python-boto in the Ubuntu Software Centre.

If you have pip installed you can install using this command

sudo pip install boto

or to upgrade (from the Ubuntu Software Centre version 2.20 to latest version 2.36)

sudo pip install boto --upgrade

[http://aws.amazon.com/sdk-for-python/](http://aws.amazon.com/sdk-for-python/)

---

### Post by Habitual on 2015-02-27
> **Qu4rk said:**
> The functionality like dropbox would be great. Owncloud as suggested. What you want to 'avoid' almost demands it.
I use s3fs to mount lots of buckets.
I use the s3scmd to sync some hosts that can't utilize fuse directly.

> **Qu4rk said:**
> S3fs has a limit of 5 GB per file. Not exactly accurate, Amazon s3 has this [limit]("http://aws.amazon.com/s3/faqs/").
Some clients that can utilize s3fs, I write directly to the mounts.
The other clients that use the s3cmd utility, use a "s3cmd sync". In the same fashion as rsync.

Who has 5G files laying around?

---

### Post by Habitual on 2015-06-05
> **dragonfly41 said:**
> There is python-boto in the Ubuntu Software Centre.

If you have pip installed you can install using this command

sudo pip install boto

or to upgrade (from the Ubuntu Software Centre version 2.20 to latest version 2.36)

sudo pip install boto --upgrade

[http://aws.amazon.com/sdk-for-python/](http://aws.amazon.com/sdk-for-python/)
I wrote [my first Python script]("http://bournetoraiseshell.com/article.php?story=20150605122607389") today using boto.ec2!
So **fast**.

I have to work on filters.
23 times it's said at [http://boto.readthedocs.org/en/latest/ref/ec2.html#module-boto.ec2.image](http://boto.readthedocs.org/en/latest/ref/ec2.html#module-boto.ec2.image)
[quote=]**filters** ([*dict*]("http://boto.readthedocs.org/en/latest/ref/dynamodb.html#boto.dynamodb.schema.Schema.dict")) &#8211; Optional filters that can be used to limit the results returned.  Filters are provided in the form of a dictionary consisting of filter names as the key and filter values as the value.  
The set of allowable filter names/values is dependent on the request being performed.  
Check the EC2 API guide for details.[/quote]
But I can't seem to interpret key/value using cheapo debug even:
```
boto.set_stream_logger('boto')
```and glancing at the output for the obvious.
I need to work on that capability.

Right now, I'm curious, and that hasn't happened in ages.

Back to the Topic, Sorry.

---

