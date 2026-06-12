---
title: "Rsync speed for local file transfers"
date: 2013-08-21
forum: General Help
---

### Post by cogset on 2013-08-21
I've been using rsync for a while now to do both full system and single directories backups,only on local devices (external USB 2.0 hard drives):generally speaking, it seems kinda slow to me,especially when backing up some files like places.sqlite (in Firefox's profile) or Thunderbird's Inbox or Sent file.

These are some examples of the file transfer speeds that I'm getting : for Thunderbird's Inbox 47.48MB/s ,for Thunderbird's Sent 36.32MB/s,for Firefox's places.sqlite  38.82MB/s -and this is even when I've sent or received no more than a couple of new messages,or when Firefox has been opened just once,I would have definitely expected things to be quicker in this case.

Reading the man page,looks like -if I got it right- rsync by default skips compressing some file types and doesn't sync files if only their timestamp has changed:for good measure,I've eliminated the -z option altogether because I've read that is actually not meant for local backups,is there anything else that I should do ? Are those transfer speeds within the norm ?

---

### Post by lukeiamyourfather on 2013-08-21
The limiting factor here will be the USB 2.0 connection to the hard disk which will max out around 50 MB/s in practice. The theoretical maximum is 60 MB/s (480**Mb** = 60**MB**, bit and byte) but I've never see anywhere close to that. If the hard disks have another interface you might try it (eSATA, FireWire, etc.). Or if the drives support USB 3.0 maybe get a USB 3.0 card for the computer.

---

### Post by cogset on 2013-08-21
Thanks-so actually what I am seeing are the real world transfer speeds that I can expect from USB 2.0 drives:interestingly,I also happen to have a 3.5" removable SATA disk that I use for less frequent backups,I'll do the next backup using the --progress option and see which transfer rate I'm getting.

Speaking of which,would  **rsync -avv --progress **be adequate,or should I consider other options ?

---

### Post by lukeiamyourfather on 2013-08-21
Yeah, most hard disks are capable of 100+ MB/s which requires an interface faster than USB 2.0 to fully utilize. I use "rsync -a --progress" for backups to local disks and have for years.

---

### Post by papibe on 2013-08-21
Hi cogset.

For local syncs, most of the time you only need something like:
```
rsync -av source/ destination
```
--progress works great to replace -v when you are transferring big files, but I found it to be "to much" when backing up regular files.

You may want to look at the option:
```
-x, --one-file-system
```
To avoid backing up network mounted directories under the source. That would avoid the typical problem of inadvertently transfer samba shares (under ~/.gvfs).

Another useful option is:
```
--include-from=/path/to/exclude.txt
```
To exclude files and directories that is not necessary to sync. This would be an example of an exclude.txt:
```
- .thumbnails/
- Downloads/
- dwhelper/
- .mozilla/firefox
- .gvfs/
- .VirtualBox/HardDisks/
+ *
```
Hope it helps.
Regards.

---

### Post by cogset on 2013-08-23
Again,very useful suggestions,thanks a lot.

Can you explain what 
```
--include-from=/path/to/exclude.txt
```does?
Does this include in the backup everything that is **not** in the exclude.txt file?

---

### Post by SeijiSensei on 2013-08-23
No, I think he meant to write "--exclude-from" rather than "--include-from".

Include-from and exclude-from work as you would expect.  Filename globs that appear in an include-from file are copied by rsync; globs that appear in exclude-from are excluded.  Usually you should exclude /proc, /run, /sys and /dev if you are backing up the entire installation since these are pseudo-filesystems created anew by the kernel at each boot.

---

### Post by cogset on 2013-09-04
A quick update:I've just done another backup using an internal SATA3 disk (well,actually a SATA6,but the motherboard only has Sata3 ports) and,aside of a couple of spikes at over 100MB/s,the higher consistent transfer rate I've seen is around  56 MB/s:so not much faster than the USB2 interface,maybe that theoretical 100+ MB/s speed is for SATA6 interfaces? Or, the disk cache may also be  a factor here,since my source hdd only has a tiny 8GB cache.

---

### Post by papibe on 2013-09-04
That is not to bad for the typical scenario:
[LIST]
[*]regular consumer driver.
[*]mechanical drives.
[*]internal disk to internal disk (or same disk).
[*]medium/full disks (more on the random-rates rates that sequential).
[/LIST]
In general, to get higher speeds, you would need some sort of raid array, or an SSD.

You can test the limit of how fast you can read and copy (without the toll of rsync), using dd. For instance, take a medium/big file (>200MB), and try:

for reading speed:
```
dd  if=./originalfile  of=/dev/null
```
and this for reading and writing speed:
```
dd  if=./originalfile  of=./newfile
```
When the copy ends, you'll see the average transfer speed.

Hope it helps.
Regards.

---

### Post by cogset on 2013-09-06
> 
[LIST]
[*]regular consumer driver.
[*]mechanical drives.
[*]internal disk to internal disk (or same disk).
[*]medium/full disks (more on the random-rates rates that sequential).
[/LIST]


Yes,all of the above apply in my case...and,as I've pointed out,my installation is on a spare HDD (it was meant to be just a test,and it worked so well that I've been using it ever since) which only has 8GB of cache.

Interesting tip about the dd test for reading/writing speed,once I'll get over the "dd fear" I think I'll give it a try-thanks.

---

