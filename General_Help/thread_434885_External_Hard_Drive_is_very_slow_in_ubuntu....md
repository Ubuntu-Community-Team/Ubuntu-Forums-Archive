---
title: "External Hard Drive is very slow in ubuntu..."
date: 2007-05-06
forum: General Help
---

### Post by juxtaposed on 2007-05-06
I have an Acomdata E5 HybridDrive Hi-Speed USB 2.0 HD500UHE5-72 (500GB). It is FAT32.

I am using Ubuntu 7.04 and the hard drive is extremely slow.I copy a DVD file over to it and it takes an hour just to copy it, aswell as slowing down the system very very much. I remember being suprised that it didn't go fast on Windows XP, but it went faster then this (I think it took 10-20 minutes to copy a DVD to the drive from my computers internal drive, but I don't remember exactly). I now think I should have formatted it with ext3, but I have way to much data on it now to keep it anywhere else (130GB of music and then there are other things, I think 200GB In all). My internal hard drive is 200GB (but actually less because of the 1024-1000 thing, and then I have OS stuff installed). This is really weird how slow it is, because it says "USB 2.0 Interface: Blazing transfers up to 480 Mbps(1). Move hundreds of megabytes of data in mere seconds.". I don't expect it to go that fast, but I do expect good performance. My computer has USB 2.0.

One more odd thing, there is a light that is blue when the hard drive is not directly in use and red when it is in use. In windows the red flashed with the blue and it looked purple-ish, but in linux the red is more constant.

Any ideas on why it is so slow, or ideas to fix it? It's really bad when trying to do things with DVDs.

Oh, another thing... I think it used to be faster under linux too. Only recently it got so slow I think. And I don't think the FAT32 needs to be defragmented; it would be stupid to fragment with 300GB of free space.

EDIT: Oh no... I think I just lost two or three DVDs, I just realised that 300MB got cut off them when I put them onto my external hard drive :/

---

### Post by MoLE on 2007-05-12
From your description, this suggests a potentially faliing external drive.  If it used to be faster, and the OS is having to put more effort into writing to disk (the red light constantly problem).

Don't forget that if you're copying DVD images to a fat32 filesystem, you can't go above the 4Gb barrier per file.

I would suggest running badblocks on the drive to see if there are any significant number of bad sectors.

---

### Post by juxtaposed on 2007-05-12
> From your description, this suggests a potentially faliing external drive. If it used to be faster, and the OS is having to put more effort into writing to disk (the red light constantly problem).

Hmmm... Another odd thing. When I transfer relativly small things (500MB-1GB), it seems to go a normal speed.

> Don't forget that if you're copying DVD images to a fat32 filesystem, you can't go above the 4Gb barrier per file.

I think it does the same thing with DVDs in VIDEO_TS format (which is split into .VOB files that are all under 1GB each).

> I would suggest running badblocks on the drive to see if there are any significant number of bad sectors.

I'll look into that - I only got the drive a few months ago. It seemed to work fine in windows when I transfered a VIDEO_TS folder that had things in it totalling around 4GB in it.

I recently found something about some sync option, and it being turned on makes hard drives really slow.

---

### Post by tgalati4 on 2007-05-13
Depending on how you copied the file:

cp
scp
ftp
sftp
sshfs
smb

Each protocol has it's own performance bottlenecks.

It's possible that a read verification is being performed and thus it will take twice as long, but be 100% reliable.

Take note of the time between Linux and Windows and see if one is twice the other.

Try the other protocols and let us know what your speeds are.

Of course, not all USB controllers are created the same.  I have heard reports of cheap controller chips (perhaps knockoffs) that don't deliver anything close to the rated speed.  

I prefer Lacie Firewire 800 drives.  They are a little faster.

---

### Post by juxtaposed on 2007-05-13
I have no idea what protocol I used. I just copied it from my file manager.

I had previously thought that smaller things didn't get affected by the slowness... But I tried to copy "jg+ms1974-10-31.sbd.19436.sbeok", which is a bit under 800MB. It started out saying it would take 2 minutes, which is fine. Then I left and came back a few minutes later and it was 30% done and it said it would be 8 more minutes.

> Take note of the time between Linux and Windows and see if one is twice the other.

I'm going to go into windows right now to try.

EDIT:

I just transfered a 700MB file to it from linux. It took 16 minutes, then said it was done. I tried to unmount the drive but it said it was busy, it took another two minutes after it said it was done for the light to turn blue. Now to check in windows.

I just transfered a 1.4GB file to it from windows. It took 2 minutes and a few seconds.

> Try the other protocols and let us know what your speeds are.

How would I do that? Is there a setting in the file manager? I thought FTP was just for internet type things.

---

### Post by tgalati4 on 2007-05-13
Open a terminal:

cp filename /mnt/Windows/mydestinationdirectory

Use a stopwatch and divide the MB by the seconds it takes to get your prompt back.

Using the Gnome File Manager (Nautilus) can be a bottleneck.  It will show that a file has been copied right away when it really hasn't.  This is an annoyance, but those who know better just use the command line to copy large files.

---

