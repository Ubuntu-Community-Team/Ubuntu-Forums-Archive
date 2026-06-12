---
title: "Large USB Transfer rate significantly slower on Ubuntu 24.04"
date: 2024-06-13
forum: General Help
---

### Post by digitding on 2024-06-13
Writing more than 5 GB to a USB  thumbdrive is much slower on 24.04 when compared to 22.04.  What action  might bring the transfer rate on 24.04 in line with that observed on  22.04?
 Using hardware of identical configuration (Dell 7020 desktop), one  loaded with Xubuntu 22.04, the other with Xubuntu 24.04 and two  identical thumb drives.  The thumb drives are formatted NTFS and cleaned  prior to each test run.  The thumb drives are referred to here as PEACH  and ARCTIC.  The data being copied resides in several files on the  primary harddrive of each system.  The size of each file ranges from a  few bytes to one at 3.3GB.
 22.04 took 9 minutes to ARCTIC and 10 minutes to PEACH
24.04 took 127 minutes to ARCTIC and 142 minutes to PEACH
 At first, 24.04 was reporting the copy function complete quite a bit  faster than that measured on 22.04.  Once the accumulated total of data  reported copied reached about 5GB, 24.04 became very slow.
 An additional pair of runs was made using PEACH after adding the command sync just prior to completion.  Those run results are:
 22.04 took 30 minutes total with sync - sync itself took 21 minutes
24.04 took 175 minutes total with sync - sync itself took 10 minutes
 A similar thumbdrive, formatted  ext4 took 47 minutes on 24.04 of which the sync was 10 minutes.  This  same ext4 formated drive took 34 minutes of which the sync was 11  minutes.

---

### Post by TheFu on 2024-06-14
So ... where to start.

In short, use journalled file systems with HDDs and SSDs, but not flash storage.
Use non-journalled file systems for flash storage.

Next, the question is which OSes must the storage physically be connected into.  That's different from network access. With network-only access, the file system should be Linux native.  The only time to use a non-native Linux file system (exFAT or NTFS) is when you must physically plug in to device to MS-Windows.

So, that brings us to the final answers.

MS-Windows + Linux with Flash storage, use exFAT.
MS-Windows + Linux with SSD/HDD storage, use NTFS.
Linux with Flash storage, use f2fs.
Linux with SSD/HDD storage, use ext4.

As for what happens when files are copied/moved between connected storage, the path that the data travels, the amount of RAM, the controllers used, the write performance and the number of write cycles for each cell all matter.

So, first, don't use a GUI to measure performance. Use CLI tools.  Use the "time" command to get exact data. Watch the disk buffers used and flushed before, during, and after the copy.  Writes don't complete until the sync is done.  GUIs don't know anything about this. They just know that the _copy() reported it was done, which would happen when the last data was read and pushed into the disk buffers.  That isn't useful.

"Similar thumbdrive" isn't the "same thumbdrive."  Every one of them that isn't treated exactly the same from the time it is pulled from the plastic wrap is different.

When the disk buffers are full, all storage operations that hit that limit will be impacted.

In storage benchmarks, f2fs is faster than ext4. The reasons for this should be obvious - it isn't writing all the protective "journal" stuff along the way.
If you want to know more about F2FS: [https://www.phoronix.com/search/F2FS](https://www.phoronix.com/search/F2FS)

If the same internal BUS is used for the copies, then there is a limit of the data that can be on the bus at 1 time.  Read the motherboard manual.  Additionally, the CPU is involved with the copies of USB storage, so the CPU and RAM access for the specific core involved in the copy to each USB controller matters.

It could be that the different kernels work in different ways.  Perhaps hunting down the changes in the kernels would show some light on the issue?  Normally, with the older release, it is possible to use the HWE kernel to get a newer kernel, that more closely matches the newer version. [https://askubuntu.com/questions/1442208/how-to-enable-hwe-on-ubuntu-22-04](https://askubuntu.com/questions/1442208/how-to-enable-hwe-on-ubuntu-22-04) explains how to install the HWE kernel.

When doing comparisons, try to use apple-to-apple comparisons.  Be exact with file sizes, number of files, exactly which USB ports are used and don't use a GUI.  Shut down all other programs that you can.  Flush the system caches and use the best file systems.  It would also be important to have the specifications for performance of the storage devices.  Both the read and write performance would matter.

There is a KDE storage testing tool that is very similar to that MS-Windows tool shown in all the flash storage reviews.

For SSDs and HDDs, it would be best to perform enterprise-like disk performance tests. Those typically would use the fio tool.  [https://arstechnica.com/gadgets/2020/02/how-fast-are-your-disks-find-out-the-open-source-way-with-fio/](https://arstechnica.com/gadgets/2020/02/how-fast-are-your-disks-find-out-the-open-source-way-with-fio/)  

And when posting, it is typical to use Mbps (megabits per second).  Be consistent and don't confuse M[COLOR="#FF0000"]B[/COLOR]ps with M[COLOR="#00FF00"]b[/COLOR]ps.

---

### Post by TheFu on 2024-06-14
I was copying some ~5GB files today. 
The source was a SATA SSD connected through a USB3.2 (red) interface on the motherboard, but the SSD enclosure was just a cheap USB3.0 (blue) one.  The target HDD is a WD-Black 8TB HDD with a 6Gb/s interface.  As you'll see, that interface is pure theory, nothing to do with the real world.

So, here's the information I captured.
```
$ du -sh File-S4E0*
5.2G    File-S4E02-str1080-huge.mkv
4.8G    File-S4E03-str1080-huge.mkv
4.8G    File-S4E04-str1080-huge.mkv
3.4G    File-S4E05-str1080-huge.mkv

```
# and the copy times in order:
```

real    2m7.146s
user    0m1.110s
sys     0m4.284s

real    1m58.245s
user    0m1.140s
sys     0m3.925s

real    1m57.804s
user    0m1.159s
sys     0m3.597s

real    2m3.514s
user    0m1.187s
sys     0m4.357s
```

"real" is clock time **not **including sync. To get the Mbps values, we take the file size in GigaBytes and divide by the number of seconds, then multiply by 8 (there are 8 bits in a byte).
```
5.2G x 8 x 1024
----------------  = 335.03 Mbps (conversion to Mbits)
    127.146

4.8G
----      = 332.54 Mbps
118.245s


4.8G
----      = 333.79 Mbps
117.804s

3.4G
----      = 225.50 Mbps
123.514s

```

So, about 330 Mbps is the reported copy performance.  This is bogus, since the drive manufacturer says it is a little over 160Mbps for writes.  This is why disk caches are so important, they make slow devices seem faster.  But eventually, the bytes need to be written to the storage.

Nothing we don't already know.

---

