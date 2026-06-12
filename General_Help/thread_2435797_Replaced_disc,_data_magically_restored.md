---
title: "Replaced disc, data magically restored"
date: 2020-01-26
forum: General Help
---

### Post by offentlig on 2020-01-26
Hi,

I've been using Ubuntu for quite some time for setting up a home multi-purpose server. But I have little experience with Ubuntu. It's installed, required applications are installed and configured, and most times when I add/change things, I need to look up how to do it.

Recently one of my hard disk drives failed. It is a 3 TB drive which is only used for backing up data from the fileshares, so I had accepted losing the data (which was recently copied to external backup anyway). I replaced the hard disk drive with a new 3 TB drive by disconnecting the failed disk, and connecting the new disk to the same power/bus cables.

When I started the server (running a recently upgraded 18.04.3 LTS) it ran what I thought was a format and/or a disk check of the new disk. I took quite a while - maybe 15 minutes; maybe more. When this was completed I logged on to the server and was very surprised to find all the drives and partitions I had before replacing the failed disk. And even the data that was/is on the failed disk are now also on the brand new drive I just installed.

This is really surprising. And it's not like its just a few megabytes. It's 1,2 TB data that has just been restored onto the new drive without the old drive being connected.

So - is this some kind of automagical Linux backup-feature?
And if so; where can I find more information about this?

Or am I loosing my marbles? :-)

Regards,
Jan

---

### Post by TheFu on 2020-01-26
Can't tell from the description, but if you formated the new disk the same as the old one, mounted it into the same location as the old one, and had an automatic backup script set to run daily, then it isn't any surprise that a backup would copy everything over.

There are 50+ different backup tools and thousands of different backup methods. From here, we have no idea what you might have setup years ago.

I'm also not convinced that what you've claimed is actually true. ;)

---

