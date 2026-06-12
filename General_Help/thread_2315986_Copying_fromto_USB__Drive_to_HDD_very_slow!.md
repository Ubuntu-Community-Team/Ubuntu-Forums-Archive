---
title: "Copying from/to USB  Drive to HDD very slow!"
date: 2016-03-04
forum: General Help
---

### Post by neil5 on 2016-03-04
Hi all, 

I've been looking into this problem for some time now and browsed the forums and net in general to try and find the solution or work-around to this big problem!

As the title states, I'm having real issues copying files between USB drives and my HDD. As a lot of people have also stated, the copy process starts off pretty quick and then slows and then eventually hangs close to the end or at 100%. A lot of people have said that it is a known issue with the kernel(s) and even though it's well known, nobody with the skills has tackled the issue. How correct is this?

As a work-around it has been suggested that a new mount is created to another location rather than the default /mnt location (if I've remembered that correctly). Although this does work to a certain degree - more so with smaller files, it is still painfully slow. It has also been suggested that the reason is because of some sort of caching that occurs before the actual copying of data, but then when the copy command kicks in the whole thing slows down. I've also heard that the copy status bar is a bit enthusiastic and that it shows the copy completed before it is anywhere near the completion of the copy and in actual fact the copy speed isn't as slow as the apparent 'hanging' would make it look. However, I have completed the same actions using Windows and the copy speed is noticeably quicker. This seems to be the one thing Windows does a lot better than Linux! 

Anyway, my question is pretty much an open question as in, how much of what I have said is true, and does anyone know of a better work-around or even when and if the 'problem' is going to be tackled?

Sorry to ramble on but I do a lot of backing up and it's really taking too long to complete. Even rsync struggles.

Thanks.

---

### Post by ajgreeny on 2016-03-04
Copying to a USB drive from an internal HDD can be slower than the reverse because of the slow write speed of some USB devices and the way the mounted drive may buffer the write, but usually from USB to HDD is as fast as the USB transfer protocol can manage to do it.

What sort of speeds are you seeing in the two directions?  Just to say "very slow" is not informative enough.

---

### Post by sudodus on 2016-03-04
> I've also heard that the copy status bar is a bit enthusiastic and that it shows the copy completed before it is anywhere near the completion of the copy and in actual fact the copy speed isn't as slow as the apparent 'hanging' would make it look.

This is maybe more true when writing to USB than reading from USB, because the data are buffered in RAM while the writing to the USB flash memory is written very slowly. This buffering also makes it important to umount a pendrive before unplugging it. Unmounting will flush the buffers alias finish writing to the device. Otherwise the file system will be corrupted. I think these problems are the same with linux and Windows.

-o-

The USB2 interface is slow, but the flash memory in standard USB pendrives is often much slower, particularly for 'many small files' because of the overhead for starting and stopping writing to each file.

For this reason it is a good idea to get a fast USB3 pendrive even if you have only USB2 ports on the computer. Of course USB3 all the way will be much faster.

It is also a problem that USB pendrives get slower after reading and writing a number of times. Then wiping the whole device (overwriting with zeros) will make it almost as fast as when it was brand new. Wiping the whole device can also reduce the risk of 'gridlocking' which makes the pendrive read-only.

Read more in the following links and links from them

[Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Howto help USB boot drives](http://ubuntuforums.org/showthread.php?t=2196858), particularly posts #6-9.

---

### Post by neil5 on 2016-03-04
Thanks for the replies.

I'll have to try and work out out slow the copying is although I'm not sure on the best way to do this although I can say that to copy 1GB of data (being one file) from HDD to USB3 (in USB 3.0 port) takes around 10 minutes. I can't see how this can be right.

Looking at that link also brought to mind the fact that writing to CD/DVD is so much quicker than writing to a USB stick/drive. This to me looks odd as well.

---

### Post by sudodus on 2016-03-04
1 GB / 10 minutes is approx 1.67 MB/s. It is way too slow unless you have a very slow USB drive.

Even the cheap but reliable SanDisk Cruzer Blade (scsi) / 4 GB will write much faster, in my test (January 22nd, 2014) 4.7 MB/s to write a 2 GB file:

>  4.7    SanDisk Cruzer Blade (scsi) / 4 GB, USB 2, good booter

- What brand, model and size is the USB drive?

- What file system is it on the USB drive (FAT32, NTFS, ext4 ...)?

What tool do you use for writing? ***cp*** or a GUI tool? You can try with a command line similar to this one, which includes sync to flush the buffers

```
time cp bigfile /path-to-target-directory-on-USB-drive; time sync
```

It will show the time for the copy command and the time for sync (flushing the buffers). I tested right now with an old SanDisk Cruzer Blade (scsi) / 4 GB, and I wrote an iso file (900 MB) to a FAT32 file system on the pendrive.

```
[COLOR="#0000FF"]ls -l /media/multimed-2/test/lubuntu/xenial-desktop-i386.iso[/COLOR]
-rw------- 1 nio nio **909115392** feb 24 18:59 /media/multimed-2/test/lubuntu/xenial-desktop-i386.iso

$ [COLOR="#0000FF"]time cp /media/multimed-2/test/lubuntu/xenial-desktop-i386.iso /media/nio/usb-target; time sync[/COLOR]

real	**3m36.340s**
user	0m0.048s
sys	0m2.384s

real	**0m3.719s**
user	0m0.000s
sys	0m0.020s
$ [COLOR="#0000FF"]bc[/COLOR]
bc 1.06.95
Copyright 1991-1994, 1997, 1998, 2000, 2004, 2006 Free Software Foundation, Inc.
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'. 
909115392/(3*60+36.34+3.7)
**[COLOR="#0000FF"]4[/COLOR][COLOR="#008000"]131[/COLOR]591**
quit
```

The resulting speed was 4.1 MB/s. In this case the time for flushing the buffers was only 3.7 seconds.

If your USB drive is a USB pendrive, and it *should* be faster according to the specs or it *used to* be faster, maybe you can wipe the whole device with mkusb and try if it will be faster after that?

See this link: [mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by neil5 on 2016-03-04
It's a Kingston 16GB FAT32 and I need to correct myself here - it's USB 2.0.

I must admit, I'm using the old copy and paste way and not the terminal. I will try what you have suggested and let you know how I get on.

Thanks for taking the time to respond, it's much appreciated.

---

### Post by sudodus on 2016-03-04
Kingston is a well-known brand name and should write faster than 1.67 MB/s, even if it is a USB 2 model. The slowest Kingston in my test wrote a big file at 3.2 MB/s

>  3.2    Kingston DataTraveler 2.0 (scsi) / 101 G2 8GB - undersized

If it were my pendrive, I would wipe the whole device. It costs some wear, but you can improve the speed to the double (maybe more depending on the model).

---

### Post by ubfan1 on 2016-03-04
Take a look at the output of lsusb -t  to see if the bus the flash stick (480M in last col) is on is shared with any USB1.1 devices (12M in last col).  Those speeds (480M/12M) are megabits, so divide by 10 for bytes, but don't expect to have anywhere near this max bus speed for your (read) transfers.  Writes to flash can be really slow, so when looking at bus issues, concentrate on reads.  There is a caching problem on copies, but it's much worse for big files (10-60G).  There are all sorts of possibilities for slow copies.

---

### Post by tom-bellas3rd on 2016-03-05
I've noticed mine tends to get slower with age as well. Especially the lower-sized usb disks. No matter what OS I am using.

---

### Post by neil5 on 2016-03-07
Ok so over the weekend I did some experimenting and came up with some very strange results, although I've done a dumb thing and not worked out speeds!! Doh!

Anyway, I've tried a Skandisk USB thumb drive (memory stick...whatever you want to call it) and 3 Kingston USB thumb drives. And they are all slow. Using the command line is quicker but only after remounting the drive(s).
I also tried a WD External Harddrive and transferred a 4GB file in quick time (again...no stats sorry) and was impressed with the copy speed. It was using the same USB port on my machine therefore drawing me to the conclusion that the port is not at fault. The WD Drive is USB 2.0 and the port is 3.0.

I just dont get it. Why would Linux copy to bigger drives so much quicker than to smaller thumb drives? Is it something to do with block or page writing (which I know very little about). I read that when re-unsing areas of a flash drive, it basically has to mess about with the pages and it takes a while - again, I can't remember exactly what I'm talking about, as you can probably figure from my ramblings, but it's in the back of my head and is bothering me. Anyway, could this be the issue, that the bigger drive basically has untouched space that can be directly copied to without a problem and that the smaller drives need 'messing about with' first?

EDIT: So Flash memory contains Planes, Blocks and Pages. The Pages are written to but cannot be deleted from directly. The Pages are inside Blocks which **can** be deleted from. But this means if there is data inside the Block you want to keep (other Pages in the Block), then this data first needs moving (re-written to somewhere else) and then the Block contents can be deleted and and re-written to - hence my very technical description earlier of messing about! It's probably best to read for yourself [here]("http://flashdba.com/2014/06/20/understanding-flash-blocks-pages-and-program-erases/").

---

### Post by sudodus on 2016-03-07
I agree. it is complicated, when you look into the details. But what you can do is to look at the device as a unit. I look at a pendrive (thumb drive, USB stick ...) as a unit with flash memory, and this memory is rather slow, often slower than the USB 2 interface. This is true in general (reading and writing, but often it is slower writing). Pendrives are particularly bad at managing many small files.

However, there are big differences between different pendrives. Some pendrives are much faster than other pendrives, as you can see in the links from post #3, and I think it is worth the extra price to get a fast pendrive.

---

### Post by neil5 on 2016-03-07
What is the best way to 'format' my Kingston USB drive to properly test the transfer rate do you think? I know it's not going to be 100% accurate as if I were using a new unused thumb drive (because of the number of writes it can handle and so on...) but it may give me a better overall understanding of it all.

I read that Windows tells the user it's finished copying files quicker because it actually caches the files on the drive itself while it finishes off copying them, but surely a copy is a copy, plus how come you can access these files straight away from another machine if this is the case?? I might be going off on a bit of a tangent here but some of the reasoning between the MS and Linux difference in transfer rate doesn't make a lot of sense to me!

---

### Post by sudodus on 2016-03-07
1. Wiping the whole device is a method that I have used successfully to restore the speed to almost the original speed.

2a. If you run the test in linux and copy one big file or many small files, you should use a linux file system, I suggest that you use the standard ext4 file system. You can use the method with ***time, cp*** and ***sync*** as described in post #5.

2b. An alternative is to use ***time, dd*** and ***sync*** and write directly to the device, I suggest 'wrapped in mkusb' to avoid mistakes. Such write processes are independent of the partition table and file systems, but it makes a difference (sometimes a big difference) if the whole pendrive was zeroised before testing, 'wipe the whole device'.

-o-

Comparison to Windows: The content is copied to the cache in RAM, and can be accessed from there. I am rather sure that the speed is limited by the flash hardware and the electronics and built-in logic in the pendrives, and I think it is independent of the operating system. I think the linux drivers are as speedy as the windows drivers for these pendrives (if writing to a native file system or without a file system).

---

