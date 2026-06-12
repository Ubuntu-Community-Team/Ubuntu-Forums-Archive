---
title: "Simple incremental backup routine"
date: 2014-10-26
forum: General Help
---

### Post by bengy103 on 2014-10-26
Hi there,

I may be in the wrong place for this for which I apologise but I have searched around the forums and had no luck.

I've just managed to get a Ubuntu 14.04 server set up and running after countless attempts over the years and 2 weeks solid since I retired and I'm absolutely delighted. I started with Ubuntu 10.04 server, maybe it was 8.04!
Talk about underestimating your own ingnorance...... Anyway

The whole point of the server was to store files, particularly the family photos, music and dvds, which it's not hard to realize are added bit by bit to a stock that we already have.

My server was never set up as a 'backup' server because I wish it to be a backup server, print server and any other type to server that I may need. Speed is not important as it's on a home network. The mix of machines cover Windows XP, Vista, 7, 8 and my very own trusty Ubuntu 12.04, which is the only one using Eth0. The others are wireless.

But I don't actually have a clue how to back things up. A look around the web did not turn up 'The beginners guide'.

On the server are folders whose path is /files/films, /files/music, /files/photos and in the first instance I'll dump the stock using a simple copy and paste routine. But what then?

In the first instance it will be from my own Ubuntu 12 which has a fixed IP 192.168.1.50 The server is on 192.168.1.52

I hope that someone will point me toward a simple tutorial of some sort, I'm sure it can't be difficult. I'll just make it look difficult.

regards,

brawd.

Ooops forgot to mention that the server has two HDDs in Raid 1.

---

### Post by sgage on 2014-10-26
I don't know of a handy tutorial. I will just mention that I use grsync, and have been very happy with it for many years now. No funny databases that get broken so that you think you've been backing up righteously, only to find out at restore time that something is screwy (I'm looking at you DejaDup). Install grsync (it's in the stock repos), get a large external HD, and experiment a while until you are confident - then set up your routine.

It's not difficult :-)

---

### Post by bengy103 on 2014-10-26
Thanks sgage,

Having a start is a big step.

---

### Post by HermanAB on 2014-10-27
You should start by reading the rsync man page.  All decent backup tools use rsync underneath and they are frequently just a bad and confusung GUI on top of a one line rsync command.

---

### Post by rbmorse on 2014-10-27
Bengy, if you're like me and find HermanAB's advice a little over your head right now and a bit off-putting, you might look at:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

There's some good treatment of the basics there and I found it very approachable.  Hope it helps you.

---

### Post by sgoranov on 2014-10-27
The incremental backup is not a solution if you are going to backup movies or music. If so then my suggestion is to take a look btsync. 
The incremental backup is for something else - files - text files for example or mysql dumps for example. In that case the best solution in my opinion is rdiff-backup.
So in conclusion, take a look btsync. It has version for windows, linux, bsd and even android.

Regards,
S.

---

### Post by bab1 on 2014-10-27
> **sgoranov said:**
> The incremental backup is not a solution if you are going to backup movies or music.

...The incremental backup is for something else - files - text files for example or mysql dumps for example. In that case the best solution in my opinion is rdiff-backup.

Sure it is.  I use it everyday.  I use rsnapshot which is a perl wrapper script for rsyc.  Rsysc is perfectly capable of providing incremental backups of large files and files that don't change much over time.  Rdiff is also good.
> 
 If so then my suggestion is to take a look btsync.

The app *btsync* is [BitTorrant Sync]("http://en.wikipedia.org/wiki/BitTorrent_Sync"); a ** proprietary binary blob that is not free to the user**.  There are plenty of FOSS applications that will work that are free and open source.  Some with a GUI such as *grsync* and some without like *rsanpshot* or *rsync* itself.

---

### Post by sgoranov on 2014-10-27
> **bab1 said:**
> Sure it is.  I use it everyday.  I use rsnapshot which is a perl wrapper script for rsyc.  Rsysc is perfectly capable of providing incremental backups of large files and files that don't change much over time.  Rdiff is also good.


What's the point to do incremental backup on large binary files like movies/pictures and music which are not changed at all?
About the btsync - yes it's a proprietary. But in the same time I'm not able to point something which is more flexible and more usable for that purpose.

Regards,
S.

---

### Post by bab1 on 2014-10-27
> **sgoranov said:**
> What's the point to do incremental backup on large binary files like movies/pictures and music which are not changed at all?
In any incremental backup routine the idea is to only **back up the files that have changed** or are new.  A full backup is what backs up everything each time. > 
About the btsync - yes it's a proprietary. But in the same time I'm not able to point something which is more flexible and more usable for that purpose.

Regards,
S.
Look harder there are plenty Open Source applications.  From the most complex (e.g. Amanda and Bacula) to the very simple (copy the files).  The problem with btsync is that you don't know what is going on because the app is just a binary blob (compiled) with no source code to look at.  Plus; and this is a BIG item, you have to pay for it!!!!  When you commit to a backup routine it should be usable for years.  I have about 5 years of backups using rsnapshot (rsync) and I can access all of that using plain old Linux command line tools.  No obsolescence.  I'm not locked into any proprietary scheme.  Digressing a bit... Some of that data I have had for 20+ years.  I have had to migrate it a few times before.

In short, incremental means just that.  You only backup that which has changed (incremented).  Rsync and all its variations can do that.  So can *[rdiff-backup]("http://www.nongnu.org/rdiff-backup/rdiff-backup.1.html")*.

---

### Post by sgoranov on 2014-10-27
As you said incremental means "store/transfer just the changes". If there is no changes there is no sense to do incremental backup. That was my point.
Proprietary against open source - I'm pass here. Don't want to start that discussion. :)

Regards,
S.

---

### Post by CaptainMark on 2014-10-27
@bab1 Bittorrent Sync is free of charge, (free as in beer)

---

### Post by bab1 on 2014-10-27
> **CaptainMark said:**
> @bab1 Bittorrent Sync is free of charge, (free as in beer)

I believe we are talking about this: [https://www.btsync.com/en/]("https://www.btsync.com/en/") which is not free at all (as in freedom or free beer).

Either way my point is there are FOSS apps that will do the job that have been around for a long time that will work for the OP's needs.

---

### Post by CaptainMark on 2014-10-27
The BitTorrent sync client is free to use [http://www.getsync.com/](http://www.getsync.com/) what you're looking at there is the price to rent server space along with it, if you use your own server, its free. I'm not advocating proprietary software, but just thought I'd point that out.

---

### Post by bab1 on 2014-10-27
> **CaptainMark said:**
> The BitTorrent sync client is free to use [http://www.getsync.com/](http://www.getsync.com/) what you're looking at there is the price to rent server space along with it, if you use your own server, its free. I'm not advocating proprietary software, but just thought I'd point that out.
Interesting.  I'll stick with rsync (rsnapshot) and rdiff-backup myself.  I understand your point abut the costs involved; both in freedom and in coin. :-)

---

### Post by bengy103 on 2014-10-31
I would point out that incremental includes my photos and music which are increased on a fairly regular basis. My apologies if my original wording was not precise enough and caused confusion.

I fitted two HDDs to this machine to rescue a failed NAS that I have been using for the past few years. It was an old banger that would not boot from a usb. That being the case I converted that exNAS box to a Raid 1 server. I salvaged the files to two old HDDs fitted to this box that were handy and I'm now trying to store those folders and files on the my server.

The current state of play is I've copied and pasted the folders, as existing on this machine, to the server. The problem being, and where I'm stuck at this moment, is that I can't establish a path from - say - my home/photos to server/photos via grsync. Grsync doesn't seem to stretch that far. I've been swotting up a bit online and found nothing for grsync servicing servers, it seems limited to my local machine - this one.

A further problem on the horizon, and one that might bring this whole discussion to an end, is that to transfer from here to the server may involve using a ssh routine, which from what I can gather online is not doable due to passwords not being passed through. Anyone know anything about this please?

regards,

brawd.

---

### Post by bab1 on 2014-10-31
> **bengy103 said:**
> ...The problem being, and where I'm stuck at this moment, is that I can't establish a path from - say - my home/photos to server/photos via grsync. Grsync doesn't seem to stretch that far. I've been swotting up a bit online and found nothing for grsync servicing servers, it seems limited to my local machine - this one.

A further problem on the horizon, and one that might bring this whole discussion to an end, is that to transfer from here to the server may involve using a ssh routine, which from what I can gather online is not doable due to passwords not being passed through. Anyone know anything about this please?

regards,

brawd.

You can use passwordless logins with ssh.  [Here]("https://www.google.com/search?q=passwordless+ssh&btnG=Go!&gws_rd=ssl#q=passwordless+ssh+ubuntu+14.04") are some sites to read up on this.

I use ssh in this manner to connect to my client machines to backup my data.

---

### Post by bengy103 on 2014-11-17
Thank you bab1, that bit went well.

Still ironing out a few puzzles. I'm not certain whether I'm enjoying the puzzle or not, though I'm coming round to thinking it's not a puzzle anymore. More of a contest between me and the server installation.

Don't forget I started this on 10.04, or maybe 8.04. I don't know what version I'll be on when it's done. Lol.

brawd.

---

### Post by matt_symes on 2014-11-17
Hi

I have also used rsync over ssh for incremental backups on the network for a long time.

I created a number of scripts so I don't have to remember the commands each time.

It can take a while to archive large files especially over wifi but I have found it incredibly flexable and totally reliable.

A good, solid tool that does have a learning curve but one that I have never regretted learning.

If you don't need something heavy weight like Bacula then it works a treat.

Just my thoughts and opinion.

edit: maybe I should edit my scripts to use nfs. That may be much quicker for large files.

Kind regards

---

