---
title: "Large Partitions - Possible Problems?"
date: 2007-02-14
forum: General Help
---

### Post by mtice on 2007-02-14
Here at work we've been tinkering with the idea of creating a massive FTP server.  We get about (currently) 50 clients sending us their financial data every night.  The total FTP transmission per client is ~ 1 gigabyte.  We need to keep that data on site for about 90 days.  Right now the work is being done by two sets of redundant 1TB machines.  Well I'm rapidly outgrowing those machines.

Well ultimately this is going to consume *massive* amounts of disk space.  We are looking into buying a big 6u unit with 24, 750GB SATA drives.  

What will end up happening is that that machine will reach the (what I've read) 16TB limit for a partition.

My question is this:  What, if any, performance problems can I expect with a partition that large?  What kind of file system should I use for a large partition?  How about raid?  I was thinking of going with a 3ware 16 port raid5/6 (if 6 is available from them) card.

Any help is appreciated.  Any suggestions for an alternative setup are welcome too.

Matt

---

### Post by kidders on 2007-02-14
Hi there,

This is an interesting post.

> **mtice said:**
> What will end up happening is that that machine will reach the (what I've read) 16TB limit for a partition.Afaik there is indeed a 16TB filesystem size limitation with Ext2/3 (8k blocks) and with some ReiserFS implementations. This doesn't apply to all filesystems though. At these sizes, ReiserFS and the Linux Extended filesystems probably aren't still fit for purpose.

Some common alternatives (both of which I've used) are JFS (with an upper limit of up to 4PB), and XFS (that supports filesytems as large as 8EB!). There are also some interesting differences in other areas, such as corruption management.

> **mtice said:**
> What, if any, performance problems can I expect with a partition that large?As you approach the ceiling on a filesystem's maximum size, two things will tend to happen:

[LIST=1]
[*]If the ceiling is by design (as is the case for Ext2/3 @ 16TB), there will be a performance penalty.
[*]Naturally, as filesystems grow, particularly across different physical devices, you'll notice a *massive* increase in failure probabilities.
[/LIST]

Although I've never come anywhere remotely close to JFS's or XFS's upper limits myself, I have used them both over RAID 1 and 5 with great success. The only negative experiences I've had have been down to my own misconfiguration of filesystem architectures or RAID parameters. I suppose it goes without saying though that a RAID scheme with some built-in redundancy is a must, given your numbers. Hehe.

> **mtice said:**
> Any suggestions for an alternative setup are welcome too.I would be slow to make any suggestions here. What you've set up (ie FTP) has a number of major advantages over many alternatives, including speed, cross-platform compatibility, resumable downloading of large files, almost no protocol overhead (wasted bandwidth), and it's old, stable & reliable.

Since you're working with financial data though, security issues may be of some concern. As I'm sure you're aware, data transmitted over a standard FTP connection is (a) very easily corruptable, and (b) very easily intercepted. Some level of key-based encryption would address both issues nicely, but you'd take a major performance hit in throughput terms.

**Edit:** Just for the sake of completion (and in case you don't already know), I should add that the Linux kernel also imposes limitations on the maximum sizes of files & filesystems. Afaik, 32-bit 2.6 kernels cap files @ 2^41 bytes (2TB), and file*systems* @ 2^73 (which is something in the region of 8,200 Exabytes, I *think*!) Naturally, 64-bit kernels support far larger numbers. Anyhow, the point is, you can have big filesystems if you want them. :-)

---

### Post by mtice on 2007-02-14
Kidders,

Thanks for the concise and quick reply.

> Some common alternatives (both of which I've used) are JFS (with an upper limit of up to 4PB), and XFS (that supports filesytems as large as 8EB!). There are also some interesting differences in other areas, such as corruption management.I was thinking of using JFS or XFS - but having never really used either of them before I wasn't sure about 1) ease of management compared to ext3/reiserfs; and 2) whether there was a better solutions.

> [LIST=1]
[*]Naturally, as filesystems grow, particularly across different physical devices, you'll notice a *massive* increase in failure probabilities.[/LIST]By that do you mean because of the sheer size of the partition the probability of failure increases?  Not necessarily because of the size per se?

> 
Since you're working with financial data though, security issues may be of some concern. As I'm sure you're aware, data transmitted over a standard FTP connection is (a) very easily corruptable, and (b) very easily intercepted. Some level of key-based encryption would address both issues nicely, but you'd take a major performance hit in throughput terms.Good point - the data is transmitted over a VPN connection.  Also regarding corruption.  The data is coming from IBM as/400's - i/5's.  There is no program included in the os/400 OS that would allow me to do any kind of checksum.  I don't suppose there's any other ways to verify data integrity?

> 
Just for the sake of completion (and in case you don't already know), I should add that the Linux kernel also imposes limitations on the maximum sizes of files & filesystems. . . .
Now I know.

Again, thanks for the info Kidders.  Any other thoughts/suggestions by you or anyone.

---

### Post by kidders on 2007-02-14
Hey again,

> **mtice said:**
> I wasn't sure about 1) ease of management compared to ext3/reiserfs; and 2) whether there was a better solutions.I wouldn't say something like Ext3 is particularly *easy* to manage, over other filesystems. I'm not completely sure what your referring to here, but tbh, most modern filesystems behave comparably (on the surface) in day-to-day operation. There *are* some other options to choose from, but personally, I would feel more comforable with a well-known (ergo well-supported), free (ie Ubuntu will keep you up to date) choice. **Edit:** It would also be important to read about how your choice handles things like journalising, error checks, etc. JFS & XFS are different, but both quite good.

> **mtice said:**
> By that do you mean because of the sheer size of the partition the probability of failure increases?  Not necessarily because of the size per se?Sorry for being so cryptic! What I *meant* to say was that there is always a chance that (either through a bug in the filesystem implementation, or other reasons), something might go wrong with the storage/accounting on a filesystem. Bigger filesystems tend to turn over more data, which means the probability of an occasional error increases ... and if (when) it happens, there's more data to corrupt!

Also, when a filesystem is using, say, two physical storage devices, the probability of failure of the entire filesystem is double that of one that uses a single device.

I imagine you knew all this already (which is why I was so brief before), but I wanted to at least mention the issue of data loss, since it's an important consideration when handling very big filesystems.

> **mtice said:**
> the data is transmitted over a VPN connection.  ....  There is no program included in the os/400 OS that would allow me to do any kind of checksum.Hmmm. In that case, encryption is probably already taken care of :-) but high-level checksumming isn't. Unfortunately, I have _zero_ experience with i5/OS / OS/400 / AS/400. Surely there is an implementation of md5sum available?

---

### Post by mtice on 2007-02-14
Kidders,

> 
Unfortunately, I have zero experience with i5/OS / OS/400 / AS/400. Surely there is an implementation of md5sum available?


Ya know, after 2 years of dealing with OS/400, I'm not really surprised of the lack of a checksum utility.  It's a rock-solid box but the OS leaves much to be desired.  But I'm going to double check just in case I've missed it.

In regards to XFS/JFS, do you have any configuration tips or links I can visit?

Much appreciated,

Matt

---

### Post by kidders on 2007-02-14
A visit to Google is the best advice I could give, really. The JFS/XFS homepages are interesting, but of limited use imo. There are plenty of benchmarks/comparisons floating around on the www though, most of which include Ext2/3, so you can make meaningful comparisons in your own mind.

One important issue with large industrial filesystems is that you really need to think carefully before actually _creating_ one. I'm sure 99% of Ubuntuers create Ext3 filesystems every day, without giving simple things like block sizes a second thought. After all, backing up & reformatting a 60GB filesystem isn't exactly rocket science, so it's easy to go back and make changes.

Obviously your situation is a little ... well ... less flexible! I would strongly advise you to look around for a HOWTO or similar document that goes into a little detail about the impact **mkfs**'s various configuration options will have on your filesystem. (Most of them don't.) Of particular importance is what your filesystem will be sitting on top of. For instance, I once set up a large (lol well it was about 2TB) XFS filesystem over a software RAID array, only to discover that it could write data almost 10 times as fast as it could read it! If I had read about & properly handled the interplay between RAID and the filesystem itself, I would've gotten it right first time. Other considerations include how much RAM you've got, and so on. It's all a question of making the right optimisations, without necessarily having the option to go back and try again.

I'm sorry this post is so weak on detail. I don't have any specific examples to draw on at this very moment, and I find it almost impossible to hold all the subtle little details in my head long enough to set a filesystem up, never mind write a post about it weeks or months later! Suffice it to say though that XFS/JFS + RAID should work perfectly for you (even if you *don't* manage to optimise it absolutely perfectly), but it is definitely worth trying.

**Edit:** On a different issue, I would be astounded if *some* kind of checksummer or hash calculator doesn't exist that you can use. (Assuming one of us can find it!) I would really recommend using one. All the calculations would add quite a bit to the amount of time required to complete a file transfer, but there's nothing like seeing reassurance of a glitch-free transfer with your own eyes.

---

### Post by mtice on 2007-02-14
Well, based upon
[http://en.wikipedia.org/wiki/Comparison_of_file_systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems")

it looks like XFS maybe my best bet.  I will dig around for HOWTO's on XFS optimization.

Thanks again Kidders,

Matt

---

