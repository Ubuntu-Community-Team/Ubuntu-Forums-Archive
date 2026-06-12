---
title: "rsync question"
date: 2017-05-15
forum: General Help
---

### Post by cc1984 on 2017-05-15
I am running Nextcloud on an Ubuntu (16.04) server to house a fairly large storage 16Tb on Raid 6. I backup the most critical data onto 6TB usb3 external drives, some of which i keep onsite and others offsite. I use rsync to copy the data over to the external drives. The total data that I copy to these drives is ~4TB. My understand is that rsync will only send the changes when copying files to save time. This is perfect for my situation since the majority of that data doesn't change that often. I've been doing this for about a year but wondering if I'm using rsync improperly because it takes much longer than I would expect to finish (~5days). I have read through the man pages and as best i can tell I'm doing it correctly. Is there another option that I can use that would speed up rsync?

Here is the rsync command that I'm using in the script that I have written: ```
rsync -a source destination
```

I know its 4Tb of data but 5 days just seems like a long time to only backup the changes. Maybe it takes that long to assess what has or has not changed though.

---

### Post by TheFu on 2017-05-16
Here's one of my example rsync's for media files with both the source and target on the same machine:
```
$ ionice rsync -av --stats --progress $EXCLUDES --delete /D/ /misc/b-3.5T/
```
Usually takes about 10 sec to run, if nothing new needs to be copied over.
Just ran it - took 3:33 to rsync 10T of source files. The system doing the work matters too. I have a 2010-ish system that cannot handle USB3 performance. The motherboard has design limitations which prevent USB3 performance.  I'm using a 2015 $50 motherboard for my rsync above. The bus architecture is designed to handle USB3 throughput.

With the progress option, I'm seeing 75-130MB/s transfers.  Most are in the 75MB/s speed. If you aren't, then perhaps the USB3 connection isn't working correctly.  Smaller files will have lower speeds due to the overhead involved in dealing with each file.

Carefully reading the rsync manpage is the only way to see the risks with some options. Pay attention to any warnings.

---

### Post by cc1984 on 2017-05-16
Thanks, the system is a 2015 low end Dell business server with way more horsepower than what I'm using. I suspect that it is copying all the data every time instead of just the changes but I'm not sure how to check for that, maybe the progress option will verify that. I'll double check the logs but it isn't throwing any errors back to the CLI.

---

### Post by TheFu on 2017-05-16
Remote rsync doesn't copy. Also, for remote rsync on a secured LAN, you might want to use a less secure encryption cypher. I use ARC4 on my LAN, but AES over the internet.

Local rsync does copy, unless you specifically tell it not to do so. This is a bad idea for very large files.  I got burned doing it with virtual machines.  It completely altered my backup methods.  It was taking 45-90 min per virtual machine. After changing to a newer method, backups are 2-4 minutes.  I use a tool that is based on rsync + rdiff = rdiff-backup. Amazing. Smart. Versioned.

---

### Post by cc1984 on 2017-05-16
Ahhh, I didn't realise it does a copy for local drives which in my case they are mounted locally. Thanks for the rdiff-backup it, I'll give it a go on my next backup!

---

### Post by TheFu on 2017-05-16
Whoa there.  rdiff-backup is different than rsync. Different uses.  I wouldn't use it on media files.  docs, images, system stuff - sure. It is perfect for that.

---

### Post by cc1984 on 2017-05-16
Ah, ok thanks.

---

### Post by HermanAB on 2017-05-16
For medium to large files, when rsync sees that a file has been modified, it calculates checksums on parts of the file on each side of the network link (when working remotely with an rsync daemon) in order to transfer only the parts that have been modified. This is an optimization only if the network bandwidth is significantly smaller than the disk bandwidth, which is usually the case. With local mounts, the “disk” bandwidth is in fact the network bandwidth, and rsync would have to read the whole file in order to determine what to copy anyway and there is no daemon on the other side to offload the remote checking to - it all happens on one machine.

So with local mounts rsync checks to see if a file is different and if so, copies the whole thing - which is much faster than reading and checking both source and destination before copying.  Note however, that rsync always checks to verify that the file was copied correctly, and if not, repairs it.  This is a very big advantage of rsync over other copy methods.

---

