---
title: "dd Input/output error writing image to sd card"
date: 2016-06-15
forum: General Help
---

### Post by nickdc on 2016-06-15
I'm trying to set up a second RaspberryPi, so have done this a couple of times before at least with no hassle.  But now I'm getting repeated errors trying to write the .img file to a  micro sd card. I've tried two different cards, one only used once, the  other brand new (but bought several months ago), both samsung, one 8Gb  the other 16. I had problems initially with the external usb card reader  I was using, so swapped that for a usb 'cradle' that came with one of  the micro cards (they slot into the end of it). I've been able to access  the cards using this and have tried both ImageWriter and, when that  crashed (non-functioning progress bar doesn't inspire confidence) tried  Etcher. Same problem: writes a bit, then finishes prematurely. So I went  a bit out of my comfort zone and tried dd on the command line. I've  tried that four or five times now and it makes more progress than the  other methods, but still ends before completion with an error message.  Here's the output from my last attempt:

```
nick@nick-build-1:~$ sudo dd if=/home/nick/RaspberryPi/Volumio1.55PI.img bs=4M | pv -s 2G | sudo dd of=/dev/sdh 
[sudo] password for nick: [sudo] password for nick:    0B 0:00:01 [   0B/s] [>     0B 0:00:07 [   0B/s] [> 

dd: writing to `/dev/sdh': Input/output error                  ]  6% ETA 9:51:38 
262625+0 records in 
262624+0 records out 
134463488 bytes (134 MB) copied, 2790.32 s, 48.2 kB/s 
 128MB 0:46:37 [  47kB/s] [=>                                 ]  6% 
```



I've  reformatted the cards (FAT32) before each new attempt and checking them  after the failed write process there are always folders and files on the  card, such as "overlays" "System Volume Information" bootcode.bin  install-kernel.sh  kernel.img  start.elf   etc  etc. Investigating with  GParted after my most recent attempt, it shows a FAT32 partition of 75Mb  (24 used) at /dev/sdh1, an "unknown" (with orange exclamation triangle)  partition of 5.85GB at /dev/sdh3 and 5.85GB unallocated.


Writing an image file to an sd card should be a piece of cake, even on old equipment like mine (self-built 3ghz P4 running Ubuntu 12.04). The  fact that the same problem appears to occur every time suggests to me  that there's something obvious I've got wrong. Can someone kindly help  me find it?

---

### Post by sudodus on 2016-06-15
I don't think you should invoke dd twice.

I think the easiest way to get things right is to use mkusb as a 'safety belt' and 'wizard' to get the dd command line right. See this link

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Good luck :-)

---

### Post by nickdc on 2016-06-15
Thanks for the advice, I'll take a look at mkusb, though if it's a hood for dd I anticipate getting the same errors. I used the second dd command after reading help pages for pv. I only turned to pv after several failures with dd on its own (and just using the command at the beginning of the string) and wanting more info on its progress.

---

### Post by sudodus on 2016-06-16
In that case maybe the SD card cannot be written to (for some other reason).

In many such cards there is a small mechanical switch, which you can use to make it read-only alias 'lock' or read/write. Check if you happened to touch it and set it in the read-only position.

There might also be other problems with the card. Check if you can get write access to it from another computer or via another adapter or slot. For example, you can try to format it (which is a write operation). See also these links:

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by nickdc on 2016-06-16
Thanks. Yes, have checked they're not locked - as I said, this is happening on two different cards, both of which are formatting ok each time after a failed burn. Both cards can be put into my tablet where they perform as expected. I'm now wondering if it's a hardware problem with my desktop pc as I've been getting sudden mouse freezes and having to do a power shutdown. I replaced the power supply a few months ago because it became very unstable and the new psu seemed to fix things, but now I'm wondering if it was a mbo or other hardware issue which is now recurring. The image writing is probably the longest running single process I use the machine for.

---

### Post by sudodus on 2016-06-16
If you can borrow another computer, maybe you can run a live DVD or USB drive and run the dd command line there, I think safer if you install ***mkusb*** (temporarily) and use it to flash from the image (img) file to the card.

It is also possible to use ***Win32 Disk Imager***, if you can borrow a computer with Windows.

[Win32DiskImager makes an Ubuntu family USB boot drive in Windows](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

It works with img files as well as with iso files.

---

### Post by nickdc on 2016-06-17
Hooray! I've had success with mkusb - many thanks, sudodus, for suggesting I try that. Worked first time, and on my old machine - didn't have to beg or borrow another pc. I certainly endorse your recommendation of mkusb, an excellent utility.

---

### Post by sudodus on 2016-06-17
I'm glad you found a solution (and thanks for marking the thread as solved to help other people) :-)

---

### Post by nickdc on 2016-06-20
Oh dear! Problem not entirely solved, and I'm not sure if I should continue here or start a new thread under mkusb....? 
Having successfully written one of the images, it still wouldn't boot my Pi. OK, so that's not entirely unexpected as others having similar problems, almost certainly related to the image file itself. So I take another micro sd card, 16gb this one, and use mkusb to write a different image of around 4gb, that others have had success with. Mkusb seemed to be doing fine, kept going much longer than all the earlier attempts with dd etc, but ended in a fail:"No space left on device". Exactly the same on a second try. I realise this would not be a failure message had I been attempting to completely wipe the whole drive, but this is an install, and I got a success message with the other image on the other card. Clearly there's plenty of space on the drive, so I'm puzzled why the process is failing.

---

### Post by sudodus on 2016-06-20
I think we can continue here (in this thread).

No space left on device indicates just that: I would assume that the target is too small for the image. ***Is this also an img file, or is it a compressed image file***, for example filename.img.gz or filename.img.xz?

If it is a 'plain' img file, the target drive must be of exactly the same size or larger. Flash cards and pendrives are not exactly the nominal size, some are slightly larger, some are slightly smaller. If you compare the size it must be measured in the same units, for example {Megabytes (base 10) or Mibibytes (base 2)} or {Gigabytes (base 10) or Gibibytes (base 2)}.

Example: 8 GB ~ 7.45 GiB

```
$ bc
bc 1.06.95
Copyright 1991-1994, 1997, 1998, 2000, 2004, 2006 Free Software Foundation, Inc.
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'. 
4000000000/1024/1024/1024
3
scale=9
4000[COLOR="#606060"]000[/COLOR]000/1024/1024/1024
3.725[COLOR="#606060"]290[/COLOR]298
8000000000/1024/1024/1024
7.450580596
16000[COLOR="#606060"]000[/COLOR]000/1024/1024/1024
14.901[COLOR="#606060"]161[/COLOR]193

```

Please post an output showing the kind of and size of the image files and of the target drives (the SD cards).

If uncompressed,

```
ls -l filename.img  # size in bytes

ls -lh filename.img  # size in human readable units / MiB or GiB
```

should do.

If compressed with xz, try ```
xz --robot --list filename.img.xz
``` to get the result in bytes,

or ```
xz -l filename.img.xz
``` to get the result in MiB.

If compressed with gzip (a gz file), the listing of the compressed size might be borked due to overflow in the representation of numbers.

The size of the SD cards can be listed with

```
sudo parted -ls  # size in MB or GB
sudo lsblk -fm  # size in MiB or GiB
```

---

### Post by nickdc on 2016-06-20
OK, thanks. Here's the results for the uncompressed image file:

```
nick@nick-build-1:~/RaspberryPi$ ls -l cirrus_logic_audio_card_all_pi_versions.img
-rw-rw-r-- 1 nick nick 4025483264 Apr  6  2015 cirrus_logic_audio_card_all_pi_versions.img
nick@nick-build-1:~/RaspberryPi$ ls -lh cirrus_logic_audio_card_all_pi_versions.img
-rw-rw-r-- 1 nick nick 3.8G Apr  6  2015 cirrus_logic_audio_card_all_pi_versions.img
```

And here are the micro-sd card results:

```

Model: Generic- SD/MMC/MS PRO (scsi)
Disk /dev/sdh: 15.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.7GB  15.7GB  primary  fat32
```

and

```
sdh                                     sdh     14.7G root  disk  brw-rw----
&#9492;&#9472;sdh1 vfat                             &#9492;&#9472;sdh1  14.7G root  disk  brw-rw----

```


Looks like there should be plenty of space.

---

### Post by sudodus on 2016-06-20
The img file is 4 GB and the target drive, the SD card, [almost] 16 GB. So there is a big margin. If the image file is an image of a drive (which I would assume), you should be able to use mkusb to install it into your 16 GB card, and there should be a lot of unallocated space after the image. There should be ***no*** message:"No space left on device".

This should be independent of what was written to the drive before.

If you tried to write to this drive earlier and had that message I wonder what happened. Could it be that it was writing to a buffer, and when it 'wanted to' start writing from the buffer to the SD card, it could not write. Are you sure that it is possible to write to the card?

The image process ***should*** work (cloning each byte from the image file to the SD card), whatever content there is in the image file. If it does not work, it could be because the card is locked, but you say it is not, and that it can be formatted. ***Can you write a file to it*** (after formatting)? ***Then I suspect that some memory cell or block is bad***, not possible to write to, so that the copying process halts, when it reaches that memory cell.

-o-

Will it work to use ***ddrescue*** and overwrite as much as possible with zeros (write from ***/dev/zero*** to the card), and use ddrescue to skip bad blocks rather than getting stuck. See this link

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

and the tutorial's ***example 1*** in ```
info ddrescue
```

where the option -n makes the first command line avoid getting stuck

```
'-n'
'--no-scrape'
     Skip the scraping phase. Avoids spending a lot of time trying to
     rescue the most difficult parts of the file.
```

```
ddrescue -f -n /dev/zero /dev/sdx logfile
```

If you get enough zeros written, maybe the automatic allocation of memory cells to logical locations might be rearranged, so that you will have at least 4 GB of good memory cells / blocks of cells in the beginning of the drive (SD card). I don't know how smart the built in program is (the program, that is built into the card), but it is worth trying.

---

### Post by nickdc on 2016-06-21
Thanks, sudodus, for your continued support. I wrote a reply yesterday, but must have closed the window before hitting "submit" - doh! Anyway, I was going to say that after the last attempt to write the image I used mkusb to wipe the whole card (using the 'special cases' option) and I assume that would be a very similar process to what you suggest re writing a whole load of zeros? After that I used gparted to create a new partition table and format the drive, than copied some image files (ie photos) across to it. all of which went smoothly without any hint of a problem anywhere. This morning I had another go at writing the .img file using mkusb. I left it running, but after an hour or so I returned to my pc to find the familiar error message. But that was not all that was on the screen (screenshot attached).  A window had opened showing the contents of "boot", which was presumably the boot partition that had just been written to the drive. There was also an error message: Unable to mount 4.0 GB File system    Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdh2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This reminded me of a thought I'd had the very first time I'd had a fail, using ImageWriter: it's as though when the write process gets to a certain stage so that there's a bootable partition appeared on the drive, Ubuntu tries to mount the drive, succeeds in opening the written boot partition but fails to open the still being written partition and causes the write process to crash. Is this possible?!!

Running out of time now, but before I post back I'll try your other suggestions. Again, many thanks for staying on the case.

[ATTACH=CONFIG]269688[/ATTACH]

---

### Post by sudodus on 2016-06-21
1. ***ddrescue*** is smarter than standard dd (which is used in mkusb). So it is worthwhile to try with ddrescue with the option -n as described in my previous post. Check if ddrescue could copy everything, or if it had to skip some memory locations. Unplug the SD card and plug it back again. Then some data might be cleared from the kernel's notion of the partition table, and it might work better to clone from the img file to the SD card.

2. Next step:  Wipe 'only' the first megabyte with mkusb. Unplug the SD card. Shutdown the computer and reboot it after one minute. Plug in the SD card and try again to clone from the img file to the SD card.

---

### Post by nickdc on 2016-06-22
OK, I've tried your suggestion with ddrescue. (I couldn't make sense of what came from "info ddrescue" - got a whole screed that seemed nothing to do with ddrescue and certainly no tutorial; same with "info gddrescue", which is what I had to actually install.)

Here's the result:

```
nick@nick-build-1:~$ sudo ddrescue -f -n /dev/zero /dev/sdh logfile


Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:    15720 MB,  errsize:       0 B,  current rate:   60686 kB/s
   ipos:    15720 MB,   errors:       0,    average rate:    8698 kB/s
   opos:    15720 MB,     time from last successful read:       0 s
Copying non-tried blocks...
ddrescue: write error: No space left on device
nick@nick-build-1:~$ 
```

This suggests to me that the whole drive was written without coming across any errors.

But I'm not sure what to do next. I'll try writing the image again using mkusb. But can you kindly clarify what you mean by "Unplug the drive": should I go through the normal "safely remove" or are you suggesting that deliberately not doing that may trigger some benefit?

Edit: I've tried again and got the same fail message. Something I've noticed is that according to the log the fail always occurs at the same point in time: 3hrs 41m 15s!

---

### Post by sudodus on 2016-06-23
When I install the package gddrescue, the program ddrescue is installed, and ```
info ddrescue
``` will offer valuable information. Use 'page down' to read the pages one after another or use 'arrow down' to move the cursor to the menu item you want to read, and press 'Enter' to go there.

Yes, it seems ddrescue could write everything. ***But did you check the logfile?*** There might be information in the logfile about problematic memory locations (maybe very small, but enough to prevent cloning the image file).

And yes again, try writing the image again using mkusb if ddrescue was successful :-)

After overwriting with zeros, there is nothing to unmount alias 'safely remove', so you can simply unplug it. Unplugging and replugging is sometimes necessary to make the linux kernel aware of the changed (created or deleted) partition table.

-o-

An alternative is to use a command line with ***ddrescue*** instead of dd (or mkusb). ***Replace /dev/zero with the img file as source file***. As usual, be very careful to get the correct drive as target.

---

### Post by nickdc on 2016-06-25
Thanks for this further help and clarification. We have visitors staying now so it may be a while before I get back on the case. I'll post how it goes when I do.

---

### Post by nickdc on 2016-07-04
Well it was a hardware issue all along! I was plugged into a powered usb hub - always highly reliable in the past, and I'm sure I used it when writing images successfully on previous occasions - and I thought I would try plugging directly into the pc instead. Immediate success and the whole write process completed very fast using mkusb, which I now highly recommend. Once again, sudodus, thanks for all your help.

---

### Post by pqwoerituytrueiwoq on 2016-07-04
Always go direct when writing images and don't go cheap on usb extension cables (learned that the hard way)
your hub may work fine but if the wire powering the hub is too thin it may not get the amperage to handle the load of writing a image reliably
even if the wire it good it may not be enough for the hub and the reader combined, a USB 3 port can help with that as it offers +40% more amperage
when it comes to using dd to write a image for my raspberry pis i use this one
[FONT=courier new]sudo dd bs=4M if=/path/to/file.img of=/dev/sdc[/FONT]

---

### Post by sudodus on 2016-07-04
Congratulations and thanks for sharing the solution :KS

---

### Post by sudodus on 2016-07-04
> **pqwoerituytrueiwoq said:**
> Always go direct when writing images and don't go cheap on usb extension cables (learned that the hard way)
your hub may work fine but if the wire powering the hub is too thin it may not get the amperage to handle the load of writing a image reliably
even if the wire it good it may not be enough for the hub and the reader combined, a USB 3 port can help with that as it offers +40% more amperage
when it comes to using dd to write a image for my raspberry pis i use this one
[FONT=courier new]sudo dd bs=4M if=/path/to/file.img of=/dev/sdc[/FONT]

Good tips :-)

But I have also had cases when a USB hub has helped things work, even a case with a pendrive that did not boot from the USB port in the computer, but booted reliably via a USB hub (even without the external power connected). So trial and error is a good method :-P

---

