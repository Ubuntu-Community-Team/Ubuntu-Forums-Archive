---
title: "Best Filesystem for Raid5?"
date: 2007-09-18
forum: General Help
---

### Post by Ares Drake on 2007-09-18
Hey folks.

I am going to build a Hardware Raid5 (no fakeraid) with 1,5TB net capacity. It won't be used for booting, but only for data storage.
Ubuntu is the only OS, so Win compatibility is not an issue.

Unfortunately I have no experience with volumes of that size. Is ext3 up to it or would you suggest to use some other filesystem?

Best Regards,
Ares

---

### Post by expatCM on 2007-09-18
I do not know how you are going to arrange your hardware, especially since you mention that it is not used for booting.  Perhaps you may want to think about a NAS and take a look at this link
[http://www.freenas.org/](http://www.freenas.org/)

---

### Post by Ares Drake on 2007-09-19
Hey expatCM,

thanks for your link. A NAS is not what I am looking for, I want to add local storage capacity to my working machine. It boots of an 2,5" HDD for low noise, so the raid will be only to store project data on it. It is a 3ware 8506 hardware raid5 with 4 Seagate 500GB disks.

However I found out, that your above mentioned freenas project (witch is beta btw and so unfortunately not suitable for my important data anyway) uses ext3 as well. 
So I suppose ext3 will work on that large 1,5TB array and I don't need to use some other less familiar FS like JFS/XFS/Reiser.

---

### Post by dabl on 2007-09-19
I've been using reiserfs for a year, on Edgy, then Feisty, and now Gutsy -- I didn't know any better than to start using it when I built my Linux system.  I built a fairly huge desktop system last year (Antec p180 case), and it has 5 hard drives in it, adding up to over a Terabyte.  It could be a server, but I don't need a server, so it's my workstation.

Anyway, there have been 2 occasions when there was a crash/hard reboot -- once from a power outage and once when I attempted to run glxgears in full screen mode on a beta OS and locked it all up (won't be doing that again!).  Both times, the reiserfs fixed itself on the next boot and I had zero loss of data.  It is slow to boot, because it does a full fsck/journal replay on each boot, but if you're building a server, you may not care about how long a bootup takes.

Two cents' worth.  :)

---

### Post by expatCM on 2007-09-19
Perhaps another reader will confirm this but I think that ext3 is good up to a volume of 2TB

---

### Post by AusIV4 on 2007-09-19
Are you just using it for long-ish term storage, or will there be constant changes to it?

I have a system that uses MythTV. I set up a RAID of about 400 GB and formatted it to ext3. Now, with MythTV I was constantly recording shows, watching shows, commercial flagging shows and transcoding them to take out the commercials - some times several of these operatings would be happening at once. It got to the point where I could expect my machine to do a hard freeze about every 24 hours. On the suggestion of a forum member, I backed up all my data and reformatted to JFS and I haven't had that problem since.

Now, the main disadvantage of JFS is that you won't be able to shrink your partition, if you ever have a reason to do that, but I'd definitely recommend JFS over ext3 for large quantities of data.

---

### Post by Ares Drake on 2007-09-20
No, the access pattern would not consist of so many and rather small operations, but rather multi-gigabyte (20-30GB) operations with mostly larger files.
However I am afraid that the ext3-fscheck at boot would take ages on a 1,5 TB volume...

Are XFS and JFS suffering the same problem or is the fscheck even necessary for data security, i.e. are JFS / XFS less secure?

---

### Post by atlfalcons866 on 2007-09-20
> **Ares Drake said:**
> No, the access pattern would not consist of so many and rather small operations, but rather multi-gigabyte (20-30GB) operations with mostly larger files.
However I am afraid that the ext3-fscheck at boot would take ages on a 1,5 TB volume...

Are XFS and JFS suffering the same problem or is the fscheck even necessary for data security, i.e. are JFS / XFS less secure?

I dont use XFS but i use JFS. It has never fscked itself on me. And i have mounted the jfs more 80 times and still hasnt fscked itself. EXT3 is just EXT2 with a journal.

---

### Post by wirelessmonkey on 2007-09-20
I have a 7.5TB Raid5 and use ReiserFS.  I've never had a problem.

---

### Post by Ares Drake on 2007-09-21
Let me just add this link for some benchmarks:
[URL="http://linuxgazette.net/122/TWDT.html#piszcz"]
http://linuxgazette.net/122/TWDT.html#piszcz[/URL]

---

### Post by Ares Drake on 2007-09-21
I have now decieded that JFS is probably best suited for my purpose. There are some more benchmarks out there at google to be found, however I found performance differences during normal usage to be rather neglectable. I just don't care if deleting 20 gigs takes a few seconds longer. So what made me swing to JFS?

    * XFS: I case of a crash / power loss, XFS might overwrite all opened files with zeros. I won't risk that data loss.
    * ReiserFS: I have read that the architecture of ReiserFS concerning its journal placement wasn't as save as other filesystems.
    * Ext3: First of, ext3 reserves 5% of the disk space for the root account. Second, it needs a lot of free disk space percentage (~10%) to avoid slowing down because of fragmentation.


But most important, the fscheck performed to verify the filesystem's integrity is much faster with JFS: [http://www.sabi.co.uk/blog/anno06-2nd.html#060424b](http://www.sabi.co.uk/blog/anno06-2nd.html#060424b).
On ext3, recovery in case of a crash can take longer than **one month** with a 1.6TB array: [http://ukai.org/b/log/debian/snapsho...-22-00-00.html](http://ukai.org/b/log/debian/snapsho...-22-00-00.html)

So thats why I will go for JFS. As a nice side effect, it is less affectable to fragmentation. Hope this helps the next one of you to get into my shoes

---

### Post by stevecs on 2007-09-27
In my opinion it depends on your filesystem size.    A filesystem to me should be as stable & boring as possible plus have the most robustness available to help fix any problems that may arrise.   In that light EXT3FS + Journal has proven to be up to that challenge numerous times (including surviving mkfs's over the array and recovering the data et al).   Problem with it is that it's only good to 8TB in size (I hear you can patch it to go to 16TB but never did that).   As for the comment on 1month for EXT3 for a fsck, I'd say that's kind of an exageration or a very special case.   Ie.   I had a ~6TB EXT3FS array w/ ~1million files on it to completely check that system (I/O on this old array was ~30MB/sec) took about 5-6 hours at worst case.  _NOT_ a fast trip, granted, but no where near a month or even a day.   

Since I went past the 8TB range I tried both XFS & JFS (never considered reiser at all since 1) way too many reports of corruption with it on google and other searches, 2) hans's attitude on forced upgrades and fixing problems, 3) too much "religion" about it (like I said I want boring).

XFS I tried numerous times and the problems with that I found were:  1) bad recovery after freezes/crashes.   I have hardened systems here w/ UPS's but that doesn't protect against kernel or other panics which leave the file system in a bad state.   In those cases would loose many files due to cachine.  2) filesystem checks when you do them takes up a _LOT_ of memory (~14GB memory to check a 70TB volume!!!)  3) a lot of bugs are still listed in critical status on the buglist for over 4 years and haven't been addressed, plus recent reports of corruption on the maillists.   4) not much of a performance difference from JFS.

ZFS: userspace, ignored.  works ok on solaris though.

ext4: ignored still experimental.   However it seems that the main maintainer for JFS is helping with ext4 as well so this may be something to check out in another year.

JFS is what I'm using now on all systems that have > 8TB volumes.   Problems:  1) limited maintainer time (no full time?)  however much less critical issues at least being reported on the lists/google, everything is well over 2+ years ago and have been fixed that I can see.    However this means if you run into something may have more wait time to get resolution.  2) _very_ prone to fragments (on a 12TB filesystem here that has been up for ~1year I have files that have well over 70,000 extents).   You can write a simple 'defragment' script youself to help fix them (ie, simple copy, check, unlink orig, copy back, check, delete copy).  however this is very time consuming, no block level defragment tool available.  3) only allows journaling of metadata not everything like ext3, so you can still loose data on a crash/freeze (recommend a forced fsck after a hard crash) you'll pretty much just lose the last file you were writing at the time however which is much better than XFS. 

Anyway, for now if you're like-minded JFS does seem to offer the most stability/robustness for >8TB systems (of if you're planing on growing to that size by resizing).  Otherwise <8TB EXT3.  

Anyway, feel free to make up your own minds if you object won't hold it against you.  :)

---

### Post by Ares Drake on 2007-10-11
Hey Steve,

thx a lot for your insights. I very much share your desire for boring but reliable operation. Thus I decieded to stick with ext3 despite my previous ideas. Still afraid that fsck was both neccessary for guaranteed data safety but would slow the boot process for hours on my raid, I went with [AutoFsck]("https://wiki.ubuntu.com/AutoFsck"), wich asks you at shutdown in case a fsck is imminent if you want to fsck during shutdown, so next time you start fsck woun't make you drink liters of cofe :)
With that solution I am very happy, will try JFS for my Myth-TV recording partition though, data safety there is of no concern to me.

Thank you all again for your help!

Greetz!

---

