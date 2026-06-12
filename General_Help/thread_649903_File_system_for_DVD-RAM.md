---
title: "File system for DVD-RAM"
date: 2007-12-25
forum: General Help
---

### Post by boga on 2007-12-25
Hi,

Since UDF write support proved to be unusable (and we'll probably have to wait for a couple of years before it is usable) I'm now wondering which file system is the best for DVD-RAM besides UDF. The DVD-RAM is used for backups thus there are few quite large files written at once. I tried ext2 and jfs and both worked but the file system for a DVD-RAM must spread writes more or less equally across the whole media and ext2 and moreover jfs surely don't.

---

### Post by TidusBlade on 2007-12-25
Never knew DVDs has file systems? Anyways, I now use K3B to burn my Discs with a Windows + Linux encoding or whatever, and works perfectly.

---

### Post by boga on 2007-12-25
The problem is that I need to add/delete files from the DVD-RAM daily so mkisofs or it's front ends are not an option.

---

### Post by disturbed1 on 2007-12-25
Been a couple of years since I've used my DVD-RAM drives/discs, but all I needed was dvd+rw-tools (for dvd-ram-control) and udftools. Now I use a PC with tons of storage. Much easier for us than having to dig through RAM discs and update this or update that. For extremely important stuff, it is redundantly archived to the file server, local PC, 2 different external hard rives, and 2 DVD-R discs. 1 each of the external hard rives and DVD-R discs are stored in a fireproof safe, with weekly trips to a safety deposit box for the other copy.


If you don't like command line programs take a look at KDVD-RAM, which *looks* like a nice GUI to the above apps. [http://www.kde-apps.org/content/show.php/KDVD-RAM+Tools?content=45888](http://www.kde-apps.org/content/show.php/KDVD-RAM+Tools?content=45888)

---

### Post by boga on 2007-12-25
disturbed1, I need to backup one home PC, I don't need a lot of storage and a DVD-RAM lasts for half a year with my backup strategy so otherwise it seems to be a perfect solution. And I don't need a GUI for backup (however a GUI for restoring would be nice but I can live without it). The problem is that with udftools I get several corrupt files (really it seems like corrupt directory entries for files) per month which is of course completely inacceptable and prevents me from adding backup script to cron.daily (where it MUST reside) and forgetting about it, so I just want to use a different file system.
BTW jfs seems to be much faster than ext2 (though of course a journaling file system is not an option for DVD-RAM).

---

### Post by disturbed1 on 2007-12-25
It could depend on how you're mounting and formating the disc or even the quality of the disc itself. Using a file system like ext2 will shorten the life of the disc greatly, as it does not space out the writing/erasing across the disc as you have noted.. You can format the disc to another file system, though it isn't recommended. A google search should pull some articles.
mke2fs -b 2048 /dev/sg0 for instance is a good start.

The basic commands I used where these, fill in what isn't there for you -
mkudffs --media-type=dvdram --udfrev=0x0150
mount -t udf -o rw

I used UDF version 1.5 because at the time I had to ensure compatibility with other OS's.

It really bothers me when I have an issue with something, but it just seems to work for everyone else. The differences that might be between what I did, and your doing are these. I had a panasonic DVD-RAM drive LF-D321 with Maxell DVD-RAM media. I never used an automatic cron job, only drag and drop, or cli cp/mv commands.

I would attempt to use the drive with a UDF file system for a few days and check out how well it works, if it doesn't work correctly, try the disc in a Windows system if possible. That will narrow done the problem. If it works fine, but your cron job produces write errors, comb through the script to find the error.

---

### Post by boga on 2007-12-26
disturbed1, thank you. The drive and the media seem to be fine (moreover the problem occurs not only with DVD-RAMs but with DVD+RWs as well and the same DVD+RW in the same drive can be written with Nautilus CD/DVD creator (that is with mkisofs) with no problem), the problem occurs when I copy files with Krusader as well, and searching the forum it seems I'm not the only one to experience UDF file corruption (though the cases are quite rare but may be just because most of the people use mkisofs). So if you say it worked fine for you and since I've experienced only directory entry corruption and never file data corruption I see only 2 explanations: 1. they've broken something since then and 2. you used rev.1.50 and I use default 2.01 and this is what I should check now.

The difference between jfs and ext2 is quite interesting. Does it happend because of extent allocation in jfs or because of caching/etc implementation? Myself I use ext3 for the root (since it seems the most "native" for Linux) and jfs for /home (since it seems to be the only (optionally) case insensitive file system supported well in Linux) but if jfs is faster on hard drives as well then may be it's worth using it (in case sensitive mode) for root too (as far as I understand it can be bootable and grub can be installed on it).

---

### Post by boga on 2007-12-26
BTW, I posted the above message an hour ago, re-formatted the DVD-RAM and started copying files to it and it only copied 1.6Gb since then, that is 500kb/s on average (DMA is on). Am I the only one to suffer from such a slow speed?

---

### Post by ahaslam on 2007-12-26
> **boga said:**
> Hi,

Since UDF write support proved to be unusable (and we'll probably have to wait for a couple of years before it is usable) I'm now wondering which file system is the best for DVD-RAM besides UDF. The DVD-RAM is used for backups thus there are few quite large files written at once. I tried ext2 and jfs and both worked but the file system for a DVD-RAM must spread writes more or less equally across the whole media and ext2 and moreover jfs surely don't.

Unusable, stf. What's your specific problem? I find the problem's often with limited guis.
[I]
PS. Sorry dude, I admit I didn't read much of the above... I can't help with packet writing.[/I]

---

### Post by boga on 2007-12-26
ahaslam, the problem is not in a GUI since I don't use one. The problem is described above: I get directory entry corruption for something like any 50th file written to DVD-RAM or DVD+RW (using packet write, not mkisofs). At this moment I'm checking a suggestion derived from the post of disturbed1 that the problem is with rev 2.01 implementation and rev.1.50 works fine (it worked fine for him).

---

### Post by disturbed1 on 2007-12-26
500kb/s sounds about right with defect management enabled. With a 1x DVD-RAM drive it would take about 2 hours for 4.2gb with defect management on. My 2x drive took ~1 hour to fill up a RAM disc. I never bothered to see if there was a way to turn this on or off in Linux.

I know that's why I quit using DVD-RAM. At the time I was using them, the price of decent DVD-R media was ~$7 each, and there where no reliable DVD-RW media, so RAM was the only option.

Have a look at these. There might be something helpful?
[http://www.g-loaded.eu/2005/11/10/packet-writing-on-cdrw-and-dvdrw-media/](http://www.g-loaded.eu/2005/11/10/packet-writing-on-cdrw-and-dvdrw-media/)
[http://www.mjmwired.net/kernel/Documentation/cdrom/packet-writing.txt](http://www.mjmwired.net/kernel/Documentation/cdrom/packet-writing.txt)

About JFS, I only use JFS across all systems. It just seems much better for me. Even beats out Reiser. But I don't run any servers that need to read/write/erase tons of small files, which is where Reiser is best.

---

### Post by boga on 2007-12-26
Thanks once again, disturbed1. So far I've written >100 files to a rev.1.50 formatted DVD-RAM and haven't encountered the problem. So either it was the problem of 2.01 implementation (than it's fine) or the problem doesn't occur on a fresh file system and is going to re-appear later. If so I'll probably compare the situation with and without packet writing and if it still doesn't help use ext2.
The problem of slowdown was at least partially the following: I used Krusader for the tests and while copying it seems to re-read the DVD-RAM directory to sync the display with the current disk state and UDF support doesn't like concurrent requests. If I leave the DVD-RAM directory it works faster, on the scale you wrote for a 2x disk.
And I'll try JFS as the root file system next time I re-install Ubuntu.

---

