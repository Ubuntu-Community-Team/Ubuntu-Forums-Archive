---
title: "the &quot;right&quot; place for mp3 files and movies"
date: 2007-09-06
forum: General Help
---

### Post by DLGandalf on 2007-09-06
in an ideal situation where multiple users can login to the computer, what would be the best location to place mp3 files and movies according to the linux file hierarchy. 

This is of course not really a problem, but I like to keep things tidy :)

---

### Post by yabbadabbadont on 2007-09-06
I have dedicated partitions for music and video.  /media/music and (wait for it...) /media/video.  :D

You just need to make sure that the directory tree and files have read permission set for everyone so that all of your users will be able to play them.

---

### Post by Dark Hornet on 2007-09-07
--same for me, I have a separate hard drive dedicated to my "media files"...all you need to do is make sure its in a location that is easy to get to, and it has the proper permissions enabled....have fun.

---

### Post by FuturePilot on 2007-09-07
I put them all on my external hard drive.

---

### Post by kesman on 2007-09-07
If you want, you can partition your HD so that /home -directory is a separate partition, and if you ever need to reinstall your system, just format other partitions than your /home, then your settings for programs and personal files will be there for your next operation system. I keep all my stuff under /home/username -dir.

---

### Post by rsambuca on 2007-09-07
> **kesman said:**
> If you want, you can partition your HD so that /home -directory is a separate partition, and if you ever need to reinstall your system, just format other partitions than your /home, then your settings for programs and personal files will be there for your next operation system. I keep all my stuff under /home/username -dir.

That doesn't help with multiuser access.

+1 to a separate partition for media files.

---

### Post by kesman on 2007-09-07
> **rsambuca said:**
> That doesn't help with multiuser access.


Wut? Everyones settings are stored under /home, and everyones files are there too, so what's the problem with multiple users on this suggestion? In the ubuntu installer just partition manually and set a bigger piece of your HD to be mounted as /home and there you go, a separate partition for personal stuff on all users.

---

### Post by rsambuca on 2007-09-07
Hey, I agree that a separate home can be a good idea, but that alone just doesn't address the OP's needs of multiuser access to the mp3 files and movies.

---

### Post by kesman on 2007-09-07
Oh I see, so there needs to be a place for everyone to store their stuff and everyone to be able to read it. I'd then suggest something like /media/storage to be a separate partition on the system, and then just mount it with some script on startup to /home/user/storage or something.

My friend has this cool system with a server on his house with HUGE hdd:s, I think there's five of them with nearly a terabyte of space. He then mounts his /home from the server, not his desktop at all. That's the best solution i've seen ever.

---

### Post by rsambuca on 2007-09-07
So it's agreed then!

---

### Post by aquavitae on 2007-09-07
There's no real need to use a separate partition.  I'd create a folder /home/shared and change its access so that anyone can read or write it.  A separate partition is a slightly tidier solution, not not really necessary.

As for fitting in to the linux file system... Generally I arrange things like this:
/etc - system config files
/home/... - user's personal docs
/media - mount points to external media (e.g. usb drives, cdroms)
/mnt - network mount points
All other locations - system files

So I have a folder /mnt/music which is symlinked to my home (/home/music) dir, but can also be shared over the network with anyone else.

---

### Post by DLGandalf on 2007-09-08
thanks for the replies

maybe I'm saying something stupid, but after some reading I think that the srv directory is a pretty good candidate too?

well anyway I'll go for the /media option and create a new logical volume with the LVM (love that thing :D )

---

