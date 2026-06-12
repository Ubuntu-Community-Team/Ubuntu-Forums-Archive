---
title: "Filesystem questions"
date: 2008-03-16
forum: General Help
---

### Post by Pogeymanz on 2008-03-16
I've always used three partitions: /, /home, swap.

I've always used ext3.

If I do a lot more partitions, like /boot, /temp, /var. How will that affect speed? Even if it isn't practically noticeable, will it theoretically make my CPU work more or less to access those files or to boot the system?

And what are the other common filesystems and what are pros and cons?
Should you use one type for /boot, and maybe a different for /temp, etc?

I don't know anything about it. I just want to learn and experiment a little.

---

### Post by Oldsoldier2003 on 2008-03-16
> **EmosSuck777 said:**
> I've always used three partitions: /, /home, swap.

I've always used ext3.

If I do a lot more partitions, like /boot, /temp, /var. How will that affect speed? Even if it isn't practically noticeable, will it theoretically make my CPU work more or less to access those files or to boot the system?

And what are the other common filesystems and what are pros and cons?
Should you use one type for /boot, and maybe a different for /temp, etc?

I don't know anything about it. I just want to learn and experiment a little.
For most users having a separate /home of a partition used for data storage only is good enough. using a /boot partition can become problematic, some distros of linux don't play well together.

As far as /var its a good idea if you are running a server as the logs can pile up fast. The biggest issue when you partition out the filesystem  like this is knowing what proportions work best for the specific application of your machine. For all intents and purposes its not worth the effort for the average user on a desktop machine.

---

### Post by HermanAB on 2008-03-16
Ext3 is very robust, but it does waste a large amount of disk space (about 7.5%).  If you use encryption on a drive then you *have* to use this one.

JFS is also robust, only wastes about 0.2% for its journal and is somewhat faster than Ext3, since there is less logging going on.

XFS is robust and good for very large files.  Designed for use as a video server.  It only uses 0.1% disk space for its logs.

ReiserFS is robust, fast and efficient, but unmaintained, so it is not recommended till Hans gets out of jail.

Hope that helps!

Herman

---

### Post by Pogeymanz on 2008-03-16
> **HermanAB said:**
> 
ReiserFS is robust, fast and efficient, but unmaintained, so it is not recommended till Hans gets out of jail.


Could you elaborate on this situation??

---

### Post by koenn on 2008-03-16
Partitioning and the ability to mount separate partitions to certain subdirectories can be convenient to add disks to a computer. So it's primaliry a disk space issue, not a performance issue
Having partitions on separate disks can improve performance some, especially with scsi (and maybe sata) disks because then you can have simultanous read and writes to separate disks. With partitions on 1 disk, the benefit is probably lost in the time it takes for the heads to move in position.

That, and if you misjudged the size of a partition, you can be running out of space in one directory and have heaps of unused space in another, and no easy way to fix it (partitioning tools may be easy to use, but it's still a potentially destructive operation)

So, especially on desktops, I would'nt count on elaborate partitioning to gain performance. It's mainly a matter of organisation and planning : a seperate /home kan save you a lot of trouble if you need or want to reinstall.

---

### Post by Pogeymanz on 2008-03-16
So, as far as partitioning, what would you do on a desktop with an 80Gig HD and a 20Gig HD? I only plan on one OS for it. So I'd like a /boot, /home, /,  and swap.

What filesystem types would you recommend for these? I don't know anything about encryption or whether or not I even want or use it now...

---

### Post by koenn on 2008-03-16
80 GB for /home
20 GB for / and swap (and /boot, if you insist). 

I'm not too sure about the size of the swap file. the rule used to be 1 or 2 times the size of RAM & more if you run apps that need lots of RAM, but that was back when 32, 64 and 128 mb RAM was common. With this rule, you end up with gigabytes of swap, I wonder if they'd ever get used, and what the benefit would be : swapping memory to disk is so slow that when you start swapping gigabytes of memory, your system would be crawling. The swapspace will protect it from a crash for lack of memory, but other than that ... ?

10-15 GB for an OS + apps is fine ; default ubuntu is approx. 5 GB
You can choose to leave some disk space on the 20GB unpartitioned, to expand the / or the swap or create a separate partition for something else in the future. 


As for choice of filesystem, HermanAB's post seems to cover that.

---

### Post by Pogeymanz on 2008-03-16
So, how should I physically attach those HD's? Does it matter which one is the slave?

---

### Post by articpenguin on 2008-03-16
Hans reiser the guy who created reiserfs is in jail. He is accused of killing his wife although her remains have not been found.



[http://en.wikipedia.org/wiki/Hans_Reiser#Court_appearances](http://en.wikipedia.org/wiki/Hans_Reiser#Court_appearances)

---

### Post by Pogeymanz on 2008-03-16
Wow. What an interesting story. Although the article says that the ReiserFS development isn't supposed to be slowed down by his arrest. So, is it really not recommended to use it?

---

### Post by articpenguin on 2008-03-17
personally i had problems with reiserfs and xfs. Id just avoid them all together. 

I use JFS. Ext3 is good but like hermanAB said its overhead is 7.5% space. I find JFSs overhead to be around 36MBs. most of JFSs overhead when first formatted is the journal which is 32MBS.

Ty tso creator of ext3 has a good explantion on why reiserfs and xfs corrupt easily.

"XFS and ReiserFS do what is called logical journaling. This means that if you modify the mod time of an inode, instead of writing the entire inode table block to the journal, they just write a note in the journal stating that "inode X now has a mod time of Y". This takes much less space, so you can pack many more journal updates into a single disk block. For filesystem benchmarks that try to saturate the filesystem's write bandwidth, and/or that also have very high levels of metadata updates, XFS and ReiserFS will tend to do much better than does ext3. Fortunately, many real-world workloads don't have this characteristic, which is why ext3 tends to perform just fine in practice in many applications, despite what would appear to be much worse benchmarks numbers, at least for some benchmarks.

The problem with logical journaling is that if you do have an unexpected power drop, and the storage system scribbles garbage on the inode table, there's no way to recover. In some cases, the only thing that is left to be done is mkfs and restore from backups. (Backups? You do keep backups, right?)"

[http://linuxmafia.com/faq/Filesystems/reiserfs.html](http://linuxmafia.com/faq/Filesystems/reiserfs.html)

---

### Post by Oldsoldier2003 on 2008-03-17
> **EmosSuck777 said:**
> Wow. What an interesting story. Although the article says that the ReiserFS development isn't supposed to be slowed down by his arrest. So, is it really not recommended to use it?

Whats worse... using an OS that kills kittens, or a FS that kills wives? At least the FS is stable, even if the development may be slow- wheras the OS grows like a virus and never was stable at all....

---

### Post by scramasax on 2008-03-17
> **EmosSuck777 said:**
> Wow. What an interesting story. Although the article says that the ReiserFS development isn't supposed to be slowed down by his arrest. So, is it really not recommended to use it?

You may want to try it.

The problem might be that ResierFS, which is the stable version that is for use right now, seems to have been left to wither on the vine in favour of Reiser4.

[http://en.wikipedia.org/wiki/Reiser4](http://en.wikipedia.org/wiki/Reiser4)

They perhaps meant to say that Resier4's development hasn't been "slowed down by his arrest".  But that's not what you'd be using, unless you were a cutting edge person who was interested in testing it and giving feedback.

I'm actually using ReiserFS myself, but I can't help being aware that I'm using something that's AFAICT has effectively been abandoned by its developers.

---

### Post by articpenguin on 2008-03-17
If hans wasnt arrested right now im pretty sure he would be on reiser 6 or 7 by now and leaving reiser3, and reiser4 unmaintained

---

### Post by bodhi.zazen on 2008-03-17
> **Oldsoldier2003 said:**
> For most users having a separate /home of a partition used for data storage only is good enough. using a /boot partition can become problematic, some distros of linux don't play well together.

As far as /var its a good idea if you are running a server as the logs can pile up fast. The biggest issue when you partition out the filesystem  like this is knowing what proportions work best for the specific application of your machine. For all intents and purposes its not worth the effort for the average user on a desktop machine.

You have to be VERY CAREFUL if you are sharing any partition between OS. I used to use a /boot partition, keep it all organized if you will. Most "modern" distors will format and re-write /boot. Sometimes even /swap (although obviously swap is no big deal, you need to update fstab / uuid is all).

Here is a nice review of file systems :

[http://www.linux.com/feature/31939](http://www.linux.com/feature/31939)

[http://www.linux.com/articles/31966](http://www.linux.com/articles/31966)

I have used all the file systems and to be honest I do not see a huge performance difference between them. There are other issues besides speed on performance testing (how often is it you write 2,000 !k files ?) (see the links for other considerations).

---

