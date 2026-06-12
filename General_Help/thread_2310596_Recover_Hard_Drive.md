---
title: "Recover Hard Drive"
date: 2016-01-20
forum: General Help
---

### Post by Chris_Bee on 2016-01-20
Hello! I'm having some trouble with my internal hard drive and was hoping you smart people could help me. So, here's all that has happened so far:

Thursday of last week, my Acer Win 7 (updated to Win 10) computer began an update. I thought it was business as usual, but I was wrong. First, it was stuck on a page that just said "restarting", after applying the update. I waited quite a while, but nothing happened. The only thing I thought I could do was a hard shutdown (since it was going to restart anyway). It started to boot like normal (showed the Acer logo and blinking cursor for a second), but then it went to a black screen. I waited hours and nothing happened. 

So, the first thing I decided to do was make a Win 10 iso bootable USB drive. After an hour of looking at the Windows logo, with its swirling loading symbol, a menu finally came up! I've tried a few different things (restore, reset, etc), but I got errors on all of them. Each time I selected an option on the Windows 10 menu, it took a good 30-45 minutes for it to go to a different page (system restore, image, etc). 

Since this didn't seem to be working, I decided I'd use my trusty Ubuntu Live USB that I made; I've owned my PC quite a while and I've had to do this one other time. I knew it'd be a simple procedure: get my data off the hard drive and do a clean Win 10 reset, but I was wrong. When I clicked my ACER hard drive on the menu, I received this error:
[I]Error mounting /dev/sda3 at /media/ubuntu/ACER: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999" "/dev/sda3" "/media/ubuntu/ACER"' exited with non-zero exit status 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read of MFT, mft=155471 count=1 br=-1: Input/output error
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.[/I]

After this, I ran through the gamut of things like ntfsfix and what have you, but that didn't help.

And now, my current position. I'm using Testdisk, but I'm sorta lost on how to use it. I chose analyze, deep search, but I have no idea what I'm supposed to be looking for:

[I]Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
     Partition                         Start             End          Size in sectors
   HPFS - NTFS               0  32 33     1529 232 47         24576000 [PQSERVICE]
   HPFS - NTFS           1529 232 48    1542 168 34            204800
   HPFS - NTFS           1542 168 35   26362 168 46      398733312 [ACER]
   HPFS - NTFS          26362 168 47  26420   7 19            921600
   HPFS - NTFS          26420  39 52   38913  37 36       200699904 [New Volume]

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continueroot@ubuntu:~# 
NTFS, blocksize=4096, 12 GB / 11 GiB[/I]


I began to try chkdsk, but it was showing it would take around 60 hours to complete a scan of a 320GB hard drive, which seems like a long time for a hard drive of that size.  If push comes to shove, I will try that, but I wanted to see if Ubuntu could help me (like usual). Thanks for reading my tale of woes. Even the smallest amount of help would be greatly appreciated. :)

---

### Post by xp15 on 2016-01-20
Do a scan and a look at the partition table, there should be one bootable *, and watch for any doubled partitions. You really should send us pics so we or me can check it and think. deep scan will try harder to find anything lost (partitions and their tables, less files).

Read this for basic understanding of the program: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
Read this to try fixing your problem: [http://www.cgsecurity.org/wiki/Data_Recovery_Examples](http://www.cgsecurity.org/wiki/Data_Recovery_Examples)
You can look at other recovery examples here: [http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_a_lost_and_damaged_NTFS](http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_a_lost_and_damaged_NTFS)

Deeper search (scan) would take long too, maybe an hour. or less, 40 minutes? our world is a mystery. You can always try chkdsk before, maybe it would take less time, and its said that chkdsk is better for ntfs stuff than linux's tools.

---

### Post by xp15 on 2016-01-28
Did it work?

---

