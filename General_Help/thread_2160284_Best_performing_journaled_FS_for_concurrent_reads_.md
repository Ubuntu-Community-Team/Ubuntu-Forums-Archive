---
title: "Best performing journaled FS for concurrent reads and writes + fast sequential reads?"
date: 2013-07-06
forum: General Help
---

### Post by User4519 on 2013-07-06
Hi :)

So I have my Ubuntu Server 12.04 running with a lot of stuff. I have a massive ZFS archive shared via NFS and CIFS, I have XBMC running in standalone mode, and I have uTorrent Server running on a dedicated 500GB HD.

My IO on that disk, at peak performance, is about 4.7 MB/s in, 600 kB/s out. Whenever I've finished downloading something, I re-check it in utserver, then create SFVs for it, then PAR2s.

Recently, I decided to make that drive a ZFS drive, since I absolutely love ZFS and its on-the-fly checksumming of data. It's also performing very well on my archive pool.

However, in this scenario it performs really, really badly. Re-checking files will take hours with downloads running simultaneously. Creating SFVs will slow everything down to a grind. PAR2s aren't that bad, as they're more CPU intensive than the are IO intensive.

So I'm looking for something else to format this drive with. My initial idea would be btrfs, as it also has block checksumming, but 1) it's still experimental, 2) I'm stuck with a 3.0 kernel for other hardware-related reasons.

I've used XFS before, and it's been absolutely awesome with regards to performance, but I also hear good things about JFS. Neither of these FSes journal data, but that's alright, seeing as how this is a drive for torrents. Any error can be fixed by a recheck and a re-download. I do, however, want metadata journaling, because I don't want .torrent files to just vanish out of thin air when the power goes.

So... I know the correct answer is to try a bunch of FSes and see which one fits best. But, being a lazy mofo, and remembering how I spent two weeks benchmarking a myriad of ZVOL+FS combinations, I'm thinking maybe someone already did this and wanted to share it with me :)

So what are your thoughts? Which FS would be right for me here? In summary, this is my usecase, prioritized for relevance:

1) Journaling needed, but not necessarily beyond metadata.
2) Simultaneous reads and writes should affect each other's performance as little as possible. utserver will be doing the reads and writes and have some kind of buffering, but not too much.
3) Sequential reads should affect the performance of 2) as little as possible while being as fast as possible. There will only ever be one thread doing sequential reads at a time.

Thanks in advance :)

Daniel

PS: I should probably add, that since there isn't a 4) in that list, it's because everything else is irrelevant. For instance, I know I can't shrink an XFS, but it doesn't matter. If there's some XATTR thing, it doesn't matter. Those three points are all that matter to me :) Cheers.

---

### Post by tgalati4 on 2013-07-06
Journaling is only required if you lose power to the drive or a sudden-event shutdown.  If you use an UPS to keep power going, and you have a reliable motherboard (uptimes going for several months at a time) then you can drop the requirement for journaling and use a higher-throughput file system.  You could add an SSD to improve throughput but you would have to write a script to move data from fast SSD's to slower spinners.  There are several proprietary disk arrays that are hybrid (SSD and spinners) that automatically migrate data from fast access to slower access depending on age of the data.  You might examine your usage patterns and write some scripts to perform a similar function.  That would give you fast, multi-thread writes and uninterrupted reads from different media.  

I think your limitation will be the SATA controller and it's limitation versus the filesystem that you choose.  Only extensive testing with your hardware will reveal the bottlenecks.  I like to use *phoronix-test-suite*  and run the disk and I/O benchmarks to determine the best utilization of hardware.

tgalati4@Mint14-Extensa ~ $ apt-cache search phoronix
phoronix-test-suite - comprehensive testing and benchmarking platform

---

### Post by User4519 on 2013-07-07
Hi tgalati4, thanks for responding :)

Well, that's kind of why I need journaling ;) This isn't server-grade hardware, and ever so often something will lock up forcing me to hit the reset switch.

SSD and all that would be total overkill for this scenario though, IMHO. I **am** just downloading to this thing, so I don't really need any more continuous throughput than what I stated (<5 MB/s writes, <1 MB/s reads). I think I'd have a hard time finding an FS that didn't support that kind of throughput, really, it's more about concurrent reads with concurrent writes, a lot of random IO, and the ability to not go completely bonkers when I on top of that add the occasional sequential reading of an entire download to create SFV files.

I actually ended up with EXT3. I ditched btrfs because my kernel is simply too old for it, XFS and JFS because I couldn't really see any proof that I **needed** the kind of performance advantages they were offering. Reiser4 would be an interesting choice, but for one it apparently uses quite a bit above average amounts of memory, and besides, it's still experimental, and again I'd be using kernel modules from 3.0. So I thought EXT3 or EXT4, which may be somewhat slower than XFS, JFS or Reiser4, but they actually also offer data journaling (which isn't **important**, but certainly is a nice freebie to have). EXT4 uses more memory than EXT3 apparently, and since I can always do an online upgrade of EXT3 to EXT4 if I'd find it to be underperforming, I simply went with EXT3. Slim, stable, robust and fairly effective.

So far I'm very pleased. Re-checks of torrents inside utserver will have literally zero impact on the speed of other downloads currently running, while finishing in a fraction of the time I experienced with ZFS. SFV creation and moving of files (i.e. fast sequential reads) outside utserver (where utorrent can't be clever about timing reads vs. the inbound and outbound traffic it's also handling) do have an impact on utserver's traffic, but nothing serious &#8212; downloads that were at ~4.7 MB/s drop to about 4.1 MB/s for the duration. Which again, is a lot shorter now, with this much simpler and leaner FS.

I'm happy with this setup, and don't plan to upgrade it to EXT4 or change it for something else. Sure, I might gain a better download speed resilience towards those sequential reads, but then again I might not, and there's not exactly an EXT4 to EXT3 *downgrade* option (as far as I'm aware of anyway). :)

Cheers! :)

Daniel

---

### Post by User4519 on 2013-07-09
Small update, just to reduce the amount of indirect dissing of ZFS. The "fraction of the time" re-checks of downloads with EXT3 compared to ZFS that I initially reported were benefiting from the fact that I'd moved all data off ZFS, reformatted and moved it back, effectively defragmenting everything 100%. After a while with new downloads, re-checks are again quite slow. That is fair, as I'm not pre-allocating files, so fragmentation will be heavy. It does, however, still cope much better with keeping internet traffic speeds high while large sequential reads are taking place.

Just FYI.

---

### Post by tgalati4 on 2013-07-09
You can see a reason for server-grade hardware--higher internal throughput on the data bus, higher throughput disk controllers, error-correcting memory, redundant power supplies, etc.  With dodgy consumer hardware, I don't think it matters what file system you use, something will end up biting you.  Only after addressing the quality of the hardware can you really assess the merits of different file system layouts.

I believe you can "downgrade" ext4 to ext3 by setting some file system tuning parameters, but I'm not sure of the syntax to do that.  Perhaps:

```
man tune2fs
```

---

### Post by User4519 on 2013-07-10
> **tgalati4 said:**
> You can see a reason for server-grade hardware--higher internal throughput on the data bus, higher throughput disk controllers, error-correcting memory, redundant power supplies, etc.  With dodgy consumer hardware, I don't think it matters what file system you use, something will end up biting you.  Only after addressing the quality of the hardware can you really assess the merits of different file system layouts.

I have to ask, and I apologize if I'm being insensitive... But are you joking? I mean, not in a general sense, but with regards to the question put forth in this thread, with the requirements so specifically laid out? Again, sorry if I seem insensitive, I'm just really really puzzled if you're **actually** suggesting something like ECC memory and SAS controllers on a server mobo for maximizing the performance on my temporary torrent download drive... And the ...

> **tgalati4 said:**
> [COLOR=#000000]*Only after addressing the quality of the hardware can you really assess the merits of different file system layouts.*[/COLOR]

... is just nonsensical?!?!?!?

> **tgalati4 said:**
> I believe you can "downgrade" ext4 to ext3 by setting some file system tuning parameters, but I'm not sure of the syntax to do that.  Perhaps:

```
man tune2fs
```

Well it actually isn't possible, and therefore the manpage doesn't mention it. But it doesn't really matter — so far EXT3 is performing quite well for me, and if I feel the need to test EXT4 in the future, I can still revert back by just backing up my date and restoring it.

Cheers,

Daniel :)

---

