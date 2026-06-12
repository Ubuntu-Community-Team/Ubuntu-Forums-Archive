---
title: "Corrupt micro SD card... or not?"
date: 2016-03-19
forum: General Help
---

### Post by Roasted on 2016-03-19
Hello friends. This post is going to sound like I'm asking for Android help, but please understand I'm not. I'm at the end of the road troubleshooting this situation on my Ubuntu laptop, and I'm questioning if what I'm seeing here on Ubuntu is somewhat conclusive to whether the Micro SD card is good, bad, or somewhere in between.

Long story short, I have a Micro SD card in my Galaxy S4. I've taken a lot of pictures and video in a short amount of time (to the tune of about 1,600 files). I use FolderSync to automatically sync everything when connected to wifi to my NAS. The catch is, two videos in particular (253 MB and 350 MB) continuously fail to transfer. As a result, I've tried other means to transfer these two video files, including:

1) Uploading to my ownCloud server
2) Uploading to my Google Drive account
3) Uploading to Dropbox
4) Firing up AirDroid and attempting to download them through a web browser
5) Transferring them manually to my NAS via Astro File Manager
6) Using a USB cable and pulling the two videos off via Nautilus
7) Putting the Micro SD card in an SD adapter and copying the videos to my laptop
8) Through terminal, copying + rsyncing the videos to my laptop
All failed, with most citing an input/output error.

It's worth noting that one video fails to play period. The other video will play on my phone just fine. 

I checked the card with GParted, but saw no errors.

Ultimately, I ran a command I found online (scary, right?) to check the SD card. Here are the results:

```
jason@mobile-hq1:/media/jason/0F28-1B01/DCIM/Camera$ dosfsck -vtr /dev/mmcblk0p1 
fsck.fat 3.0.28 (2015-05-16)
open: Permission denied
jason@mobile-hq1:/media/jason/0F28-1B01/DCIM/Camera$ sudo !!
sudo dosfsck -vtr /dev/mmcblk0p1 
[sudo] password for jason: 
fsck.fat 3.0.28 (2015-05-16)
Checking we can access the last sector of the filesystem
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
? 1
Boot sector contents:
System ID "MSWIN4.1"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
     32768 bytes per cluster
       144 reserved sectors
First FAT starts at byte 73728 (sector 144)
         2 FATs, 32 bit entries
   3895296 bytes per FAT (= 7608 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 7864320 (sector 15360)
    973696 data clusters (31906070528 bytes)
16 sectors/track, 4 heads
      2048 hidden sectors
  62331904 sectors total
/DCIM/Camera/20160131_155009.mp4
  Cluster 3429 (45977) is unreadable. Skipping it.
/DCIM/Camera/20160131_155009.mp4
  Cluster 3433 (45982) is unreadable. Skipping it.
/DCIM/Camera/20160131_155009.mp4
  Cluster 3433 (45983) is unreadable. Skipping it.
/DCIM/Camera/20160131_155009.mp4
  Cluster 3437 (45988) is unreadable. Skipping it.
/DCIM/Camera/20160131_155009.mp4
  Cluster 3437 (45989) is unreadable. Skipping it.
```

It's worth mentioning that the video listed in the output is *not* either of the problematic videos in question. It transferred fine, it plays fine, etc etc etc. Most of all, I'm wondering if anybody knows, based on this output, if I have a bad card or not. I hate to clear this card off and begin using it again if the above is a sign that the card itself is bad. I'm just not sure what to make of the "unreadable" error coupled with the fact that the video referenced in the same line is... totally fine. Any insight?

---

### Post by sudodus on 2016-03-19
***dosfsck*** is a free tool for a Microsoft file system. I have tested it and it can fix some problems. But I think that the tool in Windows can do a better job.

```
chkdsk /f
#or
chkdsk /r
```

See [this link](https://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx)

If the repair does not work, you should still be able to recover those two files with ***PhotoRec***, or should I say at least the good parts of the files.

[https://www.cgsecurity.org/](https://www.cgsecurity.org/)

Maybe some tips in the following link might help: [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

Good luck :-)

---

### Post by Roasted on 2016-03-20
Well, we got it. Right when I was about to throw in the towel, I remembered that I have an old friend called gddrescue. I found a spare drive on the shelf and USB'd it into my desktop, along with the micro SD card in an SD adapter. I ran gddrescue with the following command:

```
sudo ddrescue -r3 --force /dev/sdd /dev/sdh /root/logfile

```

(where sdd is the micro SD card, sdh is the USB'd drive it ddrescue'd to)

It found some errors, but not many. It took 4 and a half hours to complete. And in the end, the video was saved.

Man I love that utility... can't believe I didn't try it sooner. Now to see if it was just a fat32 issue (doubtful, since checks were fine) or if the micro SD card itself is bad...

---

### Post by sudodus on 2016-03-20
Congratulations, you recovered those files :-)

When ddrescue finds errors, these are bad sectors (memory cells or problems with the internal electronics or software of the card) and not file system errors.

Now that you have a backup copy (made with ddrescue), I suggest that you wipe the whole card alias overwrite it with zeros. That might make it work again (and if you are lucky it will replace the bad memory cells with spare cells). It will probably get faster too. This can be done with dd or ddrescue or with mkusb to avoid writing to the wrong drive.

---

### Post by Roasted on 2016-03-20
> **sudodus said:**
> Congratulations, you recovered those files :-)

When ddrescue finds errors, these are bad sectors (memory cells or problems with the internal electronics or software of the card) and not file system errors.

Now that you have a backup copy (made with ddrescue), I suggest that you wipe the whole card alias overwrite it with zeros. That might make it work again (and if you are lucky it will replace the bad memory cells with spare cells). It will probably get faster too. This can be done with dd or ddrescue or with mkusb to avoid writing to the wrong drive.

Good tip - thanks for that! I wasn't sure if the errors I was reading would be sector level or file system level. I thought dd/gddrescue/etc worked below the file system, so I assumed it meant a bad micro SD card (and not file system), though I wasn't sure.

I assume I can just do a /dev/zero to the card with gddrescue?

i.e.:

```
ddrescue -r3 /dev/zero /dev/sdh
```
(assuming /dev/sdh is the micro SD card)

and that would effectively zero out the drive? I assume by doing it with gddrescue, it would give me a return of error count, and as such, if I keep getting errors upon zeroing it out then I'm simply out of luck in terms of using this micro SD card error free again.

...am I on the right track with my thinking?

---

### Post by sudodus on 2016-03-20
Yes.

Please double check that it is the correct target device before hitting the enter key.

---

