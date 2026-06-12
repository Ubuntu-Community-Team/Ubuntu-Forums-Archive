---
title: "Corruption of USB flash drive upon unmounting"
date: 2015-08-07
forum: General Help
---

### Post by Curtis_Anderson on 2015-08-07
I am experiencing a strange corruption issue with a 16GB USB3 flash drive from Intenso. After copying files to the drive and subsequent un- and remounting (no pulling/ejecting required to provoke the issue), one of the following happens:
1. Everything works as expected (becomes less likely the more files are written to the drive before unmounting)
2. Random files are either missing or empty
3. The FS is corrupted

I managed to compile a test set of files that provoked the issue nearly 100% of the time on this drive. First, I made sure that this drive works reliably under Win7 using either fat32 or ntfs. Then, I ran several experiments under (x)ubuntu using various file systems. Results:
ntfs: Files missing or empty, or FS corrupted
ext4: Files missing or empty
fat32: Slow, but working reliably
udf: Fast and reliable

So you could say using udf "solved" this issue for me. With another drive that is USB2, I encountered no issues at all, so one might also assume that something is wrong with the drive. But it still bothers me that the drive seems fine with Windows, suggesting that flash drives are handled more reliably there. I also noticed that the buffering behavior using ntfs and udf is very different between Windows and Ubuntu: With Windows, copying takes longer, but ejects are almost instantaneous. Ubuntu "finishes" copying very quickly, but then takes a long time to empty the buffer when unmounting. I also noticed that this buffer-writing phase took suspiciously long in those cases where corruptions occurred. Maybe it has something to do with that?

So, what do you make of this? Should I just use udf or trash the drive instead of worrying about this? If it makes any sense, I'd be happy to make more experiments.

PS: Since this is my first post here, I'd like to say thank you for providing so much help and useful info in this forum, which has already saved me from trouble on many occasions.

---

### Post by lukeiamyourfather on 2015-08-07
The issue might be from removing the flash drive before buffered transactions have been completed. Unless mounted as sync only the writes are probably asynchronous. So while the copy file dialog is gone and says things are done the system is still writing to the flash drive behind the scenes and might be for quite a while. Before removing the drive try running the sync command which will tell Linux to write out anything buffered in memory to the drive.

---

### Post by checoimg on 2015-08-07
The GUI shouldn't finish the file copying dialog if the transfer isn't finished and copies should never be left for later if asked by the user.

OP have you tried coying the files in the command line ?

---

### Post by Curtis_Anderson on 2015-08-07
I did try command line and thunar, and it makes no difference. The time it takes cp to finish or the copy dialog do disappear seems about the same. After that, there is still drive activity (as indicated by the drive's LED). I can wait until the activity stops and then unmount instantaneously or I can unmount directly, which blocks for some time with a "writing buffer to drive" message. Again, it makes no difference in speed or outcome how I do it. As far as I know, unmount always triggers a sync first, which seems to be what happens when I unmount early and that "writing buffer" message comes up.
> [COLOR=#000000]The GUI shouldn't finish the file copying dialog if the transfer isn't finished and copies should never be left for later if asked by the user.[/COLOR]
The behavior you describe is what I get for fat32, but not for ntfs, ext4, and udf. No difference between cp and thunar or between the "weird" drive and a normal drive.

---

### Post by Curtis_Anderson on 2015-08-09
bump

---

### Post by VMC on 2015-08-09
What does sync'ing the file system buffers report?
```
sync
```

---

### Post by Curtis_Anderson on 2015-08-09
It doesn't report anything.. When I do it directly after copying, it blocks for a while and then returns silently.

---

### Post by VMC on 2015-08-09
After copying files then sync, are the files still corrupt ?

You might check log files located under "/var/log", for any aberrant behavior.

---

### Post by obake2 on 2015-08-09
I suspect that you have a "fake" USB thumb drive. Fake USB thumb drives are USB drives that report certain size (e.g. 1GB), but in reality has lower capacity. So what happens when you store files bigger than its real capacity? You lose your files, they get corrupted.  

Use F3 to analyze your USB thumb/flash drive:

See: [http://oss.digirati.com.br/f3/](http://oss.digirati.com.br/f3/)

I am not using Ubuntu Linux, but I think it is in the repositories. F3 is available in Arch and Manjaro Linux.

---

### Post by Curtis_Anderson on 2015-08-10
> [COLOR=#000000]I suspect that you have a "fake" USB thumb drive.[/COLOR]
That's what I thought at first. I had already tested it with h2testw on Windows (the original implementation of f3, I think), and it is fine.
> [COLOR=#000000]After copying files then sync, are the files still corrupt ?[/COLOR]
It looks like this: After copy+sync, thunar reports 970 files and 191 MB on the flash drive, which equals the source folder. After unmount+remount, the same folder is reported to have 430 files and 74 MB.
> [COLOR=#000000]You might check log files located under "/var/log", for any aberrant behavior.[/COLOR]
Now this is interesting. Syslog gets filled with messages, most prominently:
```
Aug 10 22:45:21 iceberg kernel: [22875.456591] sd 8:0:0:0: [sdb]  
Aug 10 22:45:21 iceberg kernel: [22875.456595] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 10 22:45:21 iceberg kernel: [22875.456596] sd 8:0:0:0: [sdb]  
Aug 10 22:45:21 iceberg kernel: [22875.456598] Sense Key : Data Protect [current] 
Aug 10 22:45:21 iceberg kernel: [22875.456600] sd 8:0:0:0: [sdb]  
Aug 10 22:45:21 iceberg kernel: [22875.456602] Add. Sense: Write protected
Aug 10 22:45:21 iceberg kernel: [22875.456604] sd 8:0:0:0: [sdb] CDB: 
Aug 10 22:45:21 iceberg kernel: [22875.456605] Write(10): 2a 00 01 28 ec 48 00 00 f0 00
Aug 10 22:45:21 iceberg kernel: [22875.456610] end_request: critical target error, dev sdb, sector 19459144
Aug 10 22:45:21 iceberg kernel: [22875.456613] Buffer I/O error on device sdb1, logical block 2432137
Aug 10 22:45:21 iceberg kernel: [22875.456614] lost page write due to I/O error on sdb1
```
It seems that the drive suddenly becomes write protected. I have attached the relevant part of the log (zipped since the uploader wouldn't accept raw). Maybe you can make some more sense of it?
This posts answer suggests that the drive is simply broken/dying:
[http://superuser.com/questions/689167/usb-stick-mysteriously-become-write-protected](http://superuser.com/questions/689167/usb-stick-mysteriously-become-write-protected)
But this still leaves me with the question of how the same broken drive can work reliably with udf or under Windows.

I am quite surprised that this data loss event is logged away so silently. I would have much preferred (and expected) a very visible error message along the lines of:
```
WARNING: Your drive just got goofed up, do NOT take it with you over the weekend and expect all your stuff to be there!
```
I don't want to act too hastily, but should I not make this a feature request somewhere? It seems essential to alert the user of such things.

EDIT: Here is a follow-up: I just ran badblocks -w on the drive and received an endless stream of errors. Almost convinced that the drive was failing all along and that I just pushed it over the edge with my testing, I rebooted into Windows, reformatted as ntfs, and ran H2testw. Surprise: The drive works perfectly without any data loss. I ran the test twice to be sure. This just doesn't make any sense.

---

### Post by Curtis_Anderson on 2015-08-12
After some more testing, I believe I am closer to what is actually happening. The problem seems to be related to ntfs. Here is what I found:
[LIST]
[*]After connecting the drive, I can run badblocks and f3 without errors, confirming that the drive is fine.
[*]Using any FS on the drive other than ntfs, there are no problems at all (contrary to what I reported earlier).
[*]If the drive is formatted to ntfs, copying a large amount of files (from terminal or with thunar) causes the messages seen in my previous post to appear in syslog. This happens after the copy is finished but before the buffer is fully written to the drive.
[*]Once this happened, I can unmount the drive's partition, but running badblocks produces more write errors in syslog (and, of course, badblocks reports drive corruption). It is clear that, when this is going on on the device level, I don't need to be surprised about seeing lots of funky stuff on FS level no matter how often I unmount/remount/reformat the partition on the drive.
[*]Physically removing the drive and reconnecting it fixes the issue and badblocks/f3 report a healthy drive once again.
[/LIST]
So, what does this mean? Have I run into a bug in ntfs-3g? In FUSE, even?

---

