---
title: "Sticky: Reiserfs (&lt;=3.6 only) and XFS users, beware..."
date: 2004-11-15
forum: General Help
---

### Post by jdong on 2004-11-15
**Do you use a filesystem other than Ext3 or Reiser4**?

It's important to know that Reiserfs and XFS, even though advertised as a "journaling filesystem" only do **metadata journaling**, not **data journaling**!

[Sources: reiserfs info derived from reiser4 site on namesys.com; XFS is from SGI's XFS FAQ]

This means that these two filesystems only guarantee that their filesystem internals remain un-corrupt after a crash, not all the data! i.e. you won't get cross-linked files or "lost clusters" (windows terms, excusez-moi), but you could get your thesis trashed with random NUL characters!

This is exactly why these two filesystems run so darn fast!

If you are having weird issues that possibly may result from data corruption, run either reiserfsck or xfs_repair from a Knoppix CD-ROM to expose any possible collected damage. As a precaution, please don't set up new systems with these FS'es... They're not worth the hassle. Their high performance often only shows up in **synthetic benchmark conditions** (i.e. reading 8 simultaneous streams from a 10GB file, creating 1 million random 1byte files, etc). Though they may occur on some weird rare high-performance servers, they certainly don't occur on your desktop!

If you're still in disbelief, simply do a stress write-and-reset test with a test partition and a test folder. It doesn't take long to start seeing text files fill up with garbage characters!


NOTE: you may turn on data journaling with reiserfs but that severly slows it down. (almost half-speed, like Ext3). You can NOT turn on data journaling with XFS, it doesn't support it!


NOTE: reiser4 does full data journaling. **full** data journaling. Not even little writeback cheats like ext3 does. **FULL** data journaling!

I started using reiser4 on test machines since its official release (reiser4progs 1.00 and higher), and have yet to corrupt a reiser4 a single time! But I can't tell you how many times I've ruined reiserfs and xfs partitions!

---

### Post by TravisNewman on 2004-11-16
OK I want to convert my partition to ext3 or reiser4 now. Currently using reiser3. Is there any way to do this without destroying my setup? Which one performs faster and more reliably?

Thanks for the warning! I was in quite the false sense of security.

---

### Post by HiddenWolf on 2004-11-16
Same for my box.

Atm, for some reason, I am running 2 ext3, and an ext2 partition.
I've got plenty of free space, so just copy-pasting the data to a new partition and changing the symlink could do it right?

Could anyone advice me on how to set up reiser4, and perhaps some partitioning help?

---

### Post by jdong on 2004-11-16
Here are rough guidelines to what I used. I had an extra partition with plenty of free space, so I could copy to new partition then copy back.

If you have more than 50% free space on your current partition and it's EXT3, go ahead and Resize it with a LiveCD of your choice (I use Kanotix). Ext3 resizing is quite a safe operation, I know some admins who script their systems to dynamically resize partitions! **WARNING:** It's only fair to warn you guys again that I've [b]ruined 2 reiserfs partitions trying to resize them[b]! A 100% failure.

**XFS can not be shrunk. It can be grown offline.**

[Note]: **DO NOT** get lazy with rebooting! Often times partition tables will not be reread and block devices won't be updated on-the-fly! Running a mkfs command on one of these newly created volumes without rebooting first **could overwrite another new partition!!**

0. Download a Kanotix LiveCD. This is a Knoppix-like LiveCD with reiser4 support. Very, very handy!
1. Compile and install a reiser4 enabled kernel. I like the **ck overloaded** kernels the best.
2. Reboot into your new kernel.
3. run **sudo cfdisk**, make the new partition. It should be slightly larger than the amount of used space (duh).
4. Reboot.
5. run **mkfs.reiser4 /dev/hdxN**, where hdxN is your newly created partition.
6. run **mkdir /mnt/new; mount /dev/hdxN /mnt/new -o noatime**.
7. **cd** to **/mnt/new**.
8. To do the copying... The most reliable command I've used is **rsync -avx / .**. This uses rsync locally, in **a**rchive mode (preserve permissions, symlinks and such), verbose mode (list files), and skipping over filesystems (to prevent copying /proc r /sys)
9. Copy over non-root filesystems with **cp -rvp /dev .**. Run this command. If you have more partitions you'd like to consolidate onto reiser4, repeat this command with other folders.
10. Boot into your new partition. Reboot. When GRUB starts, press ESC, highlight the reiser4 kernel, then press 'e'. Press 'e' again on the line that starts with kernel (hd.......). Replace **root=/dev/hdxN** with your new reiser4 root.
11. Have fun with it for a while.
12. Here's where it gets tricky; trying to copy back and create new partitions. **Boot off a Kanotix LiveCD**, to make life easier.
13. Use CFDisk, qtparted, whatever, to replace your old root filesystem with a new, blank partition. **Note: **If you're using reiser4 as your root filesystem, you **MUST** create a /boot partition.
14. mount your reiser4 partition. Copy the /boot folder over to your new 'boot' partition, set up GRUB again so that you can boot off it (grub-install, whatever)
15. Go in, re-do steps 3-9 to copy your filesystem back.

---

### Post by rbrimhall on 2004-11-16
You may want to review this article concerning journalled file systems "protecting" you from data loss...

[http://www.altlinux.com/?module=seminar&part=196](http://www.altlinux.com/?module=seminar&part=196)

"With respect to stability ReiserFS turned out to be the best. Aleksandr called this file system a good working horse that one can really depend on." (from the article)

---

### Post by anklator on 2004-11-16
god... what reiser does ubuntu include?? i was bored of using always ext3 fs so i decided to use reiserfs on ubuntu, what reiser does warty include? my fstab says reiserfs

help plz

---

### Post by rbrimhall on 2004-11-16
[QUOTE=anklator]god... what reiser does ubuntu include?? i was bored of using always ext3 fs so i decided to use reiserfs on ubuntu, what reiser does warty include? my fstab says reiserfs

help plz[/QUOTE]

reiser 3.6 (I think)... but I wouldn't be too concerned about it. It is very stable and as far as the argument that the journaling of ext3 and resier4 being more capable of "protecting" your data from power outages and hard shutdowns... it is FUD (no offense jdong). This has been hashed out many times over at LWn.net.  Resier4 does have superior journaling than resier 3.6 but just b/c you have journaling doesn't necessarily mean you are safe from data corruption... it just increases your chances of not losing data... I for one, wouldn't worry about it too much. I've use reiser3.6 for awhile now and have never had any troubles...

my two cents

---

### Post by TravisNewman on 2004-11-16
K... I'm downloading the linux-2.6.9-ck3.tar.bz2 (ck overload) as we speak. Its the full kernel source, not just the patch. I'm assuming I can just start from the default Ubuntu .config and add reiser4 support from make menuconfig, then install the kernel as normal... or would it be better to use the default ck overload .config and start from there? All I know is that everything works as it should with this kernel, and that's more than I can say for any default kernel, or any that I'VE compiled myself, and I don't want to break that.

---

### Post by TravisNewman on 2004-11-16
I'm assuming that the reiser4 support is built into the reiserfs part now?

---

### Post by LordHunter317 on 2004-11-16
[QUOTE=jdong]**Do you use a filesystem other than Ext3 or Reiser4**?

It's important to know that Reiserfs and XFS, even though advertised as a "journaling filesystem" only do **metadata journaling**, not **data journaling**![/quote]Right, and that's no cause for alarm.
I mean, XFS has only been around for years now, and you don't see all the people with SGI equipment still in play running around slaying themselves over this, do you?


> This is exactly why these two filesystems run so darn fast!Actually, there's a million more things to it than that.  Asyncronous ext2 doesn't do journaling of any sort, yet XFS and ReiserV3 manage to crush it in terms of performance.
So no, the fact they only do metadata journaling can't be why they run so fast.  It has more to do with the fact they are (resonably) intelligently designed filesystems.


> As a precaution, please don't set up new systems with these FS'es... They're not worth the hassle. Their high performance often only shows up in **synthetic benchmark conditions** (i.e. reading 8 simultaneous streams from a 10GB file, creating 1 million random 1byte files, etc).Hardly.  Tons of benchmarking (both synthetic and real-world) has been done on LKML and other places and shows both ReiserV3 and XFS trounce EXT3 in terms of performance in nearly all cases.

> If you're still in disbelief, simply do a stress write-and-reset test with a test partition and a test folder. It doesn't take long to start seeing text files fill up with garbage characters!If you run around with **any** filesystem writing data when the power goes out, eventually you're gonna get corruption.

In fact, data journalling may not even solve that problem, it may just make the window for corruption smaller, at least w.r.t IDE drives.  The kernel has no way of knowing if an IDE drive actually wrote at it's cache if told to, so the data may go caput when the power fails anyway.  FreeBSD even disabled IDE caching for a few releases by default because of this, until the community cried out about it.

> NOTE: reiser4 does full data journaling. **full** data journaling. Not even little writeback cheats like ext3 does. **FULL** data journaling!So?  There's no real-world proof that it's a gain for desktop systems, or even server systems.   I'm not convinced that writing everything to disk twice actually gives you any more data integrity.   Namesys doesn't give any compelling reasons as to why, and when you think about how data is written out, you realize doing it twice doesn't make a whole lot of sense, there's still a window for corruption. 

Plus, the write penalites may not be worth it.  We don't know how severe it is because the Namesys folks haven't produced full benchmarks against synchronous ext2.  The few benchmarks they show aren't very conclusive about it's performance IMHO.
Plus, there are no XFS benchmarks.


>  But I can't tell you how many times I've ruined reiserfs and xfs partitions!How many and under what conditions?  I suspect there were other mitigating factors causing the data loss, and not just because they don't do full data journaling as you suggest.
FWIW, I've blown out data on every filesystem I've used: FAT (in all it's incarnations), XFS, ReiserFS, ext2, ext3, NTFS, ODS-11v2 (VMS, HA!).
So I don't see the point.

> **[b][sic] XFS can not be shrunk. It can be grown offline.** Incorrect.  XFS can be grown online.  In fact, you have to AFAIK.

Moreover, Hans Reiser himself on LKML has pointed out that ReiserV4 isn't production ready for everyone yet, specifically wrt to stability.

So all I see here is a bunch of paranoia and lack of technical understanding, to be frank.

Given that XFS has been around a lot longer than any version of ReiserFS and has a much wider test base across Irix and Linux, I know what filesystem I'm using for my data, including the multi-TB disk array attached to my Altix.

---

### Post by jdong on 2004-11-16
Thanks for clarifying a few things.

I personally have come to love XFS, and still use it quite extensively (though I'm beginning to phase a few XFS partitions in favor of Reiser4)

As far as the situations where I've corrupted reiserfs and XFS, it's usually something rudimentary, like power outages. Files in /var and /etc have random NUL characters left in them. There were times with reiserfs that all the contents of /usr went into /lost+found.

Though a few statements may not be technically sound, I'm just reporting what I've seen before, as a fair warning.

From what I've read, XFS 1.1 seems to fix a lot of its issues with metadata corruption, which I'm glad to hear. But still, it was with 1.1 that I had my dpkg /var files corrupted, forcing me to reinstall a production server.

---

### Post by jdong on 2004-11-16
For those trying to test Reiser4, the **ck** patches are different from the ck overloaded patch: [http://kem.p.lodz.pl/~peter/cko/](http://kem.p.lodz.pl/~peter/cko/)

And I don't think I ever said that reiser4 or ext3 will guarantee all your data is secure; I just said that reiser4 and ext3 have a lesser chance of data corruption, from my experience.

---

### Post by TravisNewman on 2004-11-16
jdong (or anyone who knows): does the ck overloaded kernel support the reiser4 filesystem through the reiserfs entry in the config, or is it somewhere else that I have yet to find?

Edit: And now I'm having new trouble, possibly related to what you said about reiser4 and needing a /boot parition. I'm running reiserfs 3.6 (or whatever is included with Warty) on my main parition. When I reboot into the kernel it says that it can't mount root fs /dev/hda1 because of a block error, but I can boot into the 2.6.8.1-k7 kernel I installed through apt-get. Is that the problem? If so I suppose I can just do everything from the livecd. Not a huge deal, I just want to make sure I can get this to work before I hose things.

---

### Post by LordHunter317 on 2004-11-16
[QUOTE=jdong]Thanks for clarifying a few things.
As far as the situations where I've corrupted reiserfs and XFS, it's usually something rudimentary, like power outages. [/quote]A power outage is hardly rudimentary when it comes to preserving data.  Most filesystems will be corrupted in some fashion if they're writing data out and the power flicks off.

As for losing data over a power outage after the data has been written out, that's normally a bug.  More than a few of those have plauged reiser and XFS, for different reasons.

> There were times with reiserfs that all the contents of /usr went into /lost+found.Sounds like borked superblock or tree-head to me, which is not normal (this wasn't early 2.4, was it?).

> Though a few statements may not be technically sound, I'm just reporting what I've seen before, as a fair warning.Yes, but your parading XFS and and ReiserV3 as unsafe and ReiserV4 as a herald creates lots of unnecessary concern among other people.  Uneeded concern, which is my problem.

---

### Post by jdong on 2004-11-16
I'm sorry. I've just been getting into reiser4 lately, reading that paper and studying its sources. I guess I got carried away there!

Regarding the other issues, these are all recent experiences, most on Debian with vanilla 2.6.6 - 2.6.8.1 kernels.

The most recent one was dpkg's state files being corrupted with random NUL characters, with XFS.


To users trying the ck overloaded kernel, reiser4 is a separate entry from reiserfs. Make sure that **4k stacks are OFF**: reiser4 doesn't compile with those, and menuconfig will hide reiser4 if you chose 4k stacks.

---

### Post by zenwhen on 2004-11-16
I run Reiser 3.6 myself. I have never had an issue with data corruption though I know it is a possibility. There's nothing I can't stand to lose that I dont backup on DVD+RW. 

**Protip:**
Don't trust any filesystem.

---

### Post by jdong on 2004-11-16
[QUOTE=zenwhen]**Protip:**
Don't trust any filesystem.[/QUOTE]
Absolutely. However, it's frustrating when a web server goes down, random files have been slaughtered, and you're trying to bring it offline to restore a backup all while 3,000 miles away.

---

### Post by zenwhen on 2004-11-16
I've just never seen, or even heard talk of this massive and probable random file corruption you are speaking of. 

Do you have a link to some sort of study or group of Linux professionals who back this up? Im not saying you don't know what you're talking about. I'm saying I'd like to see if others are saying the same.

---

### Post by jwb on 2004-11-17
I just try to make sure I don't have anything important on my computer. That's a sure-fire way to prevent critical data loss.

Frees up more time for posting here or eating doughnuts or stuff.

---

### Post by HiddenWolf on 2004-11-17
[QUOTE=jwb]I just try to make sure I don't have anything important on my computer. That's a sure-fire way to prevent critical data loss.

Frees up more time for posting here or eating doughnuts or stuff.[/QUOTE]

So, anything important gets done on a typewriter then?

---

### Post by regeya on 2004-12-01
[QUOTE=LordHunter317]Yes, but your parading XFS and and ReiserV3 as unsafe and ReiserV4 as a herald creates lots of unnecessary concern among other people.  Uneeded concern, which is my problem.[/QUOTE]

My thoughts exactly.  Maybe the Gentoo over-tweaking crowd thinks that Reiser4 is a good idea right now, but really, anyone who convinces anyone else to commit important data to Reiser4 right now needs to be shot.  I can't stress this enough:  step away from the computer and put your hands where I can see them if you're about to run Reiser4 on a production machine!

I've been running Reiser3 on this machine, and due to some minor problems, I'll be switching back to ext3.  With btree hashes, ext3 is plenty fast for me, and I haven't lost any data to anything other than human error and hardware failure with ext3 since it became part of the stable kernel.

Maybe once reiser4 is stable I'll go running to it.  Those new golly-gee-whiz features had better be awesome, though.

---

### Post by arctic on 2004-12-01
[QUOTE=HiddenWolf]So, anything important gets done on a typewriter then?[/QUOTE] :lol:

i have used reiserfs on my boxes since more than two years now and i never had suffered from lost data after a crash (i actually managed to get my box crashing maybe five times due to hacking in that time...), so i don't see the point to panic about reiserfs. also: if you do not mess up your system it will not crash = you will not loose data. and there are still cd/dvd-bruners. ;)

just my two cents.

---

