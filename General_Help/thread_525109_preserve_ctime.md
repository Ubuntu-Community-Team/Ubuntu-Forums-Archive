---
title: "preserve ctime"
date: 2007-08-13
forum: General Help
---

### Post by spin2cool on 2007-08-13
I understand the basic usage of rsync, but I seem to be running into an odd error.  

I'm setting up a server in a different city, so that I have offsite incremetal backups using rsync.  In order to speed things up, I 'preseeded' a directory on the remote hard drive with a copy of all my files.  The idea here is that when I go to rsync for the first time, I won't have to copy 100GB of data, just the incremental changes.

Unfortunately, rsync tries to copy every file, rather than recognizing that the files already exist on the remote side.  This is because the modified time (or ctime) for each file has changed.   I know that I can use rsync -c to use checksums, but that's 7 kinds of slow.  

So is there a way to copy my files initially while preserving ctimes?

---

### Post by pmg on 2007-08-14
The ctime is sometimes called the inode change time.  The file modification time is the mtime.  I assume that's the one you're interested in.  In order to get file modification time copied you need to include the rsync -t flag.  The -c flag tells it to always use checksuns and not trust timestamps.  Without that, it only checks file content if the file time and/or size is different.  Even so, rsync would list each file as "updated' but it wouldn't copy all the data back over, unless the -W (or --whole-file) option is used.

Could you post what rsync flags/options you're using?  That might help explain what's happening.

---

### Post by spin2cool on 2007-08-14
I see where the confusion is coming in - I'm not using rsync to do the initial copy of my files.  I have a 250 GB hard drive sitting unused in the other city right now, so I was going to bring my current hard drive there, copy the files manually, then bring my hard drive back home and begin using normal rsyncing between the two copies.

Here's the command I'm using:

rsync -avzh -e "ssh -i /home/username/.ssh/rsync-key" --delete --exclude-from=/home/username/.rsync/exclude /media/data username@remotehost:/media/data/ 

In the verbose output, I'm seeing a listing of every file slowly scrolling by, despite there being an exact copy present in the same directory on the remote filesystem.

I can also check the ctime of the files in that directory, and the ctime of the files is updated after the rsync, indicating to me that the file was copied over.  Am I wrong here?

---

### Post by pmg on 2007-08-14
Are you sure that's "h" in the options?  That's to request help.  (Maybe it's -H?)

Other then that, what you have should work.  However it's going to put what is in /media/data on the local system under the directory /media/data/ on the remote system.  That is, there will be a /media/data/data directory on the remote system.  Is that what you are expecting?  I wonder if you want:
rsync -avzh -e "ssh -i /home/username/.ssh/rsync-key" --delete --exclude-from=/home/username/.rsync/exclude /media/data/ username@remotehost:/media/data

Some other thoughts in case that's not it:
Have you tried it without the -z.  Maybe the slowness you are seeing is from the overhead of doing compression, rather then the slowness of the network?

Have you compared the directory entries on both ends?  Do they look the same?  The rsync verbose output does list every file if there is any update needed to the file - even if it's just changing something like the timestamp or owner.  

Are you running as root, or with sudo?  The -a option implies -o and -g, to perserve owner and group, but  that requires superuser (root).

---

### Post by spin2cool on 2007-08-14
-  yeah, media/data/data is where I want the directory (long story, old naming decisions) 

-  the -h option is actually 'human readable', at least on my systems (feisty)

*"The rsync verbose output does list every file if there is any update needed to the file - even if it's just changing something like the timestamp or owner."*

hrmmm - that's one possibility.   What's the easiest way to test if all the data is actually being transferred?

---

### Post by spin2cool on 2007-08-14
I think I resolved the problem.  It looks like the files weren't actually being copied, but they were having their timestamps, groups and such updated.  Combining that activity with the -z zipping option made everything slow enough that I convinced myself that everything was being copied. 

Thanks for the help, pmg.

---

### Post by pmg on 2007-08-14
Glad you figured it out.  I've seen the same thing with compression - that it can slow things down so much that it's worse then transmitting the extra bytes.

re: -h - You're right about that.  I was looking at the rsync help on an older Redhat system, which had rsync 2.6.3 on it.  When I checked my newer system (feisty) with rsync 2.6.9, -h changed meanings.

---

