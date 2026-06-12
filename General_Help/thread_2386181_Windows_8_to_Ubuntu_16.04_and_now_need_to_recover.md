---
title: "Windows 8 to Ubuntu 16.04 and now need to recover"
date: 2018-03-01
forum: General Help
---

### Post by brevardo2 on 2018-03-01
I've had Windows 8 on my Dell desktop for four years. I must have obtained some kind of malware or Virus recently and wasn't able to boot up Windows 8 anymore. I thought I could install Ubunti 16.04 without wiping out my Windows 8 files and I chose the LVM install option ( as it didn't warn me it would erase everything ) Once I booted into Ubuntu I noticed I had 975 gb of free space available on a 1 TB hard drive which made me realize I had just wiped out my 1 TB of important Wndows 8 files. I have tried G Parted ( with Gpart ) and then scanned my system for four hours only to say it couldn't find any of my Windows files. I've been now messing with Testdisk and it just doesn't seem to work. It's not user-friednly and it's just not showing any windows files after I've tried several attempts. It kicks me out too easily after spending an hour doing a search. What do you recommend? My hard drive still has 975 gb available as I'm afraid to write on the hard drive or download anything new thinking there may still be a way to recover my files. I'm wondering if Testdisk would have worked and just isn't for me due to whatever the malware was I must have picked up. I keep getting messages that my data is corrupted when I ran the TestDisk and PhotoRec programs. I've tried to select several options that looks like 650 GB or another result that shows 540gb and I can never get it to show recognizable files. If I called Dell and was able to re install Windows back and write over the Ubuntu 16.04 install would that be an option? I really screwed up by trusting this LVM option as I didn't think it would erase everything. Any help would be greatly appreciated. I don't want to touch the 975 gb of free space because I'm trying to keep hope there may be a way to recover the files.

---

### Post by oldfred on 2018-03-03
LVM install has always been a full drive install. It works as an alternative to fixed partitions.
Did you also use encryption?

Anything that is overwritten is gone. And one more reason we always suggest good backups and updating that backup just before any system change.

If testdisk disk deeper search did not find old partitions and data in the old partitions, you can try photorec.
But photorec only finds files by type, not full file name. I used photorec to find some .txt files and it found them. It also found the deleted copies and I just had a very long list of .txt files. I had to compare files, compare each file with older backup and figure out which was newest version. Many weeks as side project.

Others have posted that Windows NTFS tools may work better.

 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

