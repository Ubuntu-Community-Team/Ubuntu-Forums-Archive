---
title: "Rsync only if any changes"
date: 2023-04-03
forum: General Help
---

### Post by johndid on 2023-04-03
Hi,
I have a script to backup a folder to an external HDD. 

```

#!/bin/bash
date=$(date +%d.%m.%Y-%H.%M.%S)
budir="/media/ryback/"

mkdir $budir/$date

rsync -ahvP /home/luke/docker/ "$budir"/"$date"


```
I also set up a cronjob to run it every day at 4:30 PM

It creates a new folder with my files inside in my external HDD every day

Everything works as expected and I could be happy with it already. But, I was wondering if
I can make some improvements. In particular, I'd like to run the script only if there are some changes in the folder to backup, and I'd like
also to tar/zip the folder.
Could you help figure it out please.
Thanks

---

### Post by TheFu on 2023-04-03
rsync behaves different based on whether the source and target files are both local or only 1 is.
If you only want copies of changed files ... but still want new directories, then rsync is the wrong tool.  You want a versioning backup tool, that used librsync to create versioned backups, but uses hardlinks for the files that are the same.  There are a number of those tools.

[LIST]
[*]Back-in-Time [https://www.howtogeek.com/110138/how-to-back-up-your-linux-system-with-back-in-time/](https://www.howtogeek.com/110138/how-to-back-up-your-linux-system-with-back-in-time/)
[*]rsnapshot [https://ubuntu.com/server/docs/tools-rsnapshot](https://ubuntu.com/server/docs/tools-rsnapshot)
[*]
[/LIST]
are a few.  You can roll your own using **cp -H** and **rsync**, if you like.  Most UNIX scripting books have a script muck like rsnapshot in an appendix.  With rsnapshot, we gain 25+ yrs of knowledge for free.

I use **rdiff-backup**, which is like the RCS version control system, sorta.  It handles versioning using reverse difference files. The latest backup looks like a mirror. Older versions only contain diff.gz files of the actual differences in each file. Additionally, rdiff-backup captures owner, group, permissions, ACLs, xattrs, which the hardlink methods to not.

Of course, if you are doing software development, then you really should be using something like a git repo and not a backup technique.

I thing rsnapshot is most like what you are doing today.  If you don't know about "hard links", wikipedia has a good article on that.

Let the tools handle the versioning for you.  They do a good job.

---

### Post by johndid on 2023-04-03
hi
 rsnapshot sounds to be the way to go here, especially because it would run on a headless Ubuntu server.
 Apart from that, even though I'm not an expert it also seems to be a more reliable tool.

A couple of questions if you don't mind.
Would rsnapshot replace rsync as a backup tool completely, or I need to use rsync too at the same time somehow anyway?
what do you mean with** "With rsnapshot, we gain 25+ yrs of knowledge for free"**? :-)

Thank you

---

### Post by TheFu on 2023-04-03
> **johndid said:**
> hi
 rsnapshot sounds to be the way to go here, especially because it would run on a headless Ubuntu server.
 Apart from that, even though I'm not an expert it also seems to be a more reliable tool.
It is a tool specifically created to do exactly what you seem to desire.

> **johndid said:**
> 
A couple of questions if you don't mind.
Would rsnapshot replace rsync as a backup tool completely, or I need to use rsync too at the same time somehow anyway?
Inside rsnapshot, it will use rsync. You won't need to use it directly.

> **johndid said:**
> 
what do you mean with** "With rsnapshot, we gain 25+ yrs of knowledge for free"**? :-)

Just that the tool has been around a long time and some really smart people have been incrementally improving it all this time.  Use their knowledge and skill. "Stand on the shoulders of giants."  Leverage their work.  That's a common thing in the F/LOSS world.

Whenever something isn't working the way I think it should, that usually means I'm missing something, not that the tool is broken.  The longer a tool has been used, the less likely there are for major errors.

---

### Post by johndid on 2023-04-04
Very good!

Thank you

by the way, Which program/service do you use to backup to cloud services?
I heard great things about Rclone.

---

### Post by TheFu on 2023-04-04
> **johndid said:**
> Very good!

Thank you

by the way, Which program/service do you use to backup to cloud services?
I heard great things about Rclone.

**I don't use cloudy anything. I don't trust them with anything important.** A friend and I each swapped HDDs full of our initial backups and use rsync to mirror our rdiff-backup areas.  The first backup would be too large to do that, but everyone after that is relatively tiny. 

Obviously, huge media files are not included in the remote backups.  Actually, huge media files get backed up using rsync, not rdiff-backup. This is because I don't have 50TB just for backups.  For over a decade, the rdiff-backup storage has been less than 1.5TB for hold 10-20 systems worth of backups.

---

### Post by HermanAB on 2023-04-05
Just to explain something:
Scripts like rsnapshot or rdiff-backup, Mike Rubel’s, or my own script ([https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)) all use rsync underneath to do the dirty work.  Rsync is very good when configured the right way.

If you would look at the rsync man page (which requires some patience, but it is quite readable), you would see that it has multiple methods to check whether something changed: The file date(s), size or CRC.

The Update option commands rsync to only copy a file if different, based on one or more of these three parameters. The date and size are quick to verify, but the CRC needs to be calculated at both the source and destination, so it is slower (and since it has to read the files to calculate the CRC, it can just as well copy them over again, so some tools keep a database of sums).

As for Hard Links, these are merely an additional name for the same file. So when two copies of a file in your backup set are identical, you only need another name entry for it in the directory tree, which saves a tremendous amount of space.  There will still be some duplications when two files are the same, but with different owners.  These scripts handle that issue properly with the cp command. (There is another utility called hardlink, which doesn’t, which is the cause of all the warnings about hard links).

To really understand it, you need to spend a day or three playing with these tools. It is not a simple problem, with many gotchas and corner cases.

---

### Post by TheFu on 2023-04-05
I'd never heard of **hardlink** before.  Interesting.  I've always used **ln** for both hard and symbolic (-s) linking.  cp has the ability to create hardlinks too.

I've tested hardlinks and rsync and backup tools that leverage both.  The owner is ignored in the comparison.  If 2 files are hardlinked together, there will only be 1 owner.

Also, the extremely efficient way that rsync handles small changes to files in the '-u' option (or -avz which is a common backups set of options), is different between local and network copies.  If there are any differences between 2 local files, then the source is fully copied to the target.  But when there are differences between a local and network file, librsync's magic happens so that only changed blocks are transferred.

Of course, I could be missing something, but I did test these things again in 2023 to verify the problem still exists.

---

### Post by SeijiSensei on 2023-04-05
In answer to your original question, your method creates a fresh empty directory for each night's backup. So rsync will transfer all the source files every day.

If you want rsync to only transfer changed files, you must direct it to use the same directory each day. Then it can compare the files and transfer only the changed ones.

I use a variant of your approach. I back up to dated directories, so each day's backup is inclusive. In my script I delete the oldest one after eight days. (I also keep one backup each month.)

---

### Post by TheFu on 2023-04-05
> **SeijiSensei said:**
>  
I use a variant of your approach. I back up to dated directories, so each day's backup is inclusive. In my script I delete the oldest one after eight days. (I also keep one backup each month.)

Back-in-Time does a variant of this, but with hardlinking between versions.  It worked for my 80+ yr old mother AND she was able to understand it. It is harder to write what it does for backup set management, but suffice it to say that there are more backup sets closer to "now" and fewer as the time in the past is further ... er .... back -in- time.  So, 13 months ago, there is only 1 backup set. That's the annual one that gets kept forever (without manual deletion). For the last 12 months, there is always 1 monthly backup set.  For the last month, there are always weekly backup sets. (One of those weekly sets is also the monthly one and when it is 13 months old, that monthly set will be THE annual backup being retained.  See how it works?  Those are the defaults. We can customize how many, how often and for how long backup sets are retained.  The versioning is automatic.

rsnapshot does hardlink-based versioning, just with daily/weekly backups. It uses librsync/rsync.  The versioning is part of the tool's management.

Everyone creates their own backup script when they first start.  Then they realize that some really smart people have been doing backups since the 1970s and their scripts have been improved a little at a time since then.  N-I-H syndrome isn't always bad, provided the end result meets your needs.

When it comes to any backup tool, the best advice I have is to set it up on a small directory like /etc/ and run a few backups, make some small changes, run some more backups, then go look at the target directory for the the backup data.  Usually it is pretty clear what is happening.

---

### Post by johndid on 2023-04-06
> **HermanAB said:**
> Just to explain something:
Scripts like rsnapshot or rdiff-backup, Mike Rubel’s, or my own script ([https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)) all use rsync underneath to do the dirty work.  Rsync is very good when configured the right way.
..

To really understand it, you need to spend a day or three playing with these tools. It is not a simple problem, with many gotchas and corner cases.

I always enjoy to learn new things about linux and computer science in general, but I don't have solid skills/backgrounds about that to go deeper into certains matters.
I found out about rnaspshot and have been trying it for a couple of days, and it has always done a great job, and more importantly, it does exactly what I was looking for.
Thus, there is no point for me to reinvent the wheel, especially if we are talking about a very reliable tool. I think that I will stick with it 
Thanks for the link and your thoughts.

---

