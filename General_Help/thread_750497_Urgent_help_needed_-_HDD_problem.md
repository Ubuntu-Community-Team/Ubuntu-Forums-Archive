---
title: "Urgent help needed - HDD problem"
date: 2008-04-09
forum: General Help
---

### Post by dr.koljan on 2008-04-09
Today I booted into Ubuntu 7.10 LiveCD to resize my partitions. I wanted to shrink my Windows partition to grow the partition for downloads. The download partition is to the right of the Windows partition.

The shrinking process went well and didn't take much time, however, when it came to growing, GParted started copying the contents of the download partition. This time it was very slow and the process was probably going to take several hours (35GB). Therefore, I decided to watch some videos on YouTube in the meanwhile.

Unfortunately, Ubuntu locked up (I guess it's the Gnash's fault) so I could nothing but reboot. I did try Alt-Ctrl-Backspace'ing and I am sure the resizing process halted anyway. Since GParted was copying and not moving, the contents of the partition should be intact. I need a suggestion on what I should do now, as I am afraid of even mounting this partition. I'm currently in Ubuntu LIveCD.

Thanks in advance.

---

### Post by dannyboy79 on 2008-04-09
within the livecd, does 
sudo fdisk -l
return a valid partition table? if so, you should be able to use partimage and make an image of that partition so that it's backed up safely. then you can resize without worry. if you don't have a place to back up the partimage file to, then I am not sure what to tell you. before I work on repartitioning, I always boot up a live cd, then mount my external usb hard drive, and use 

sudo cp --preserve --recursive /* /media/usbdrive/
that way everything mounted on / will be backed up. change the / to where ever you mounted the partition to. I don't think it would be bad to mount it, just don't change anything on it.

that's just my 2 cents, please don't hold me responsible for any bad things that may happen.

---

### Post by phidia on 2008-04-09
Many of the top posters here recommend [system rescue cd]("http://www.sysresccd.org/Main_Page").

---

### Post by dr.koljan on 2008-04-09
"sudo fdisk -l" gave me what I expected, however, when I try to mount this partition, I get this:

```

$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
```

Should I do as I am told?

---

### Post by wolfen69 on 2008-04-09
PartedMagic [www.partedmagic.com](www.partedmagic.com) is a great live cd for partitioning/resizing. *and* you are automatically root.

---

### Post by wolfen69 on 2008-04-09
put xp cd in, and go to recovery console. run- chkdsk /f

---

### Post by dr.koljan on 2008-04-09
Ugh, I guess I should have used SystemRescueCD. After I rebooted into Windows XP it started "checking drives for consistency", finding errors and "fixing" them. Now I have lost at least a half of my files. Well, at least I have learned a lesson for future - never use Ubuntu LiveCD for partition editing, and never trust Windows.

---

### Post by dannyboy79 on 2008-04-11
no, i think the leason would be that whenever you're shrinking or resizing NTFS partitions (or any filesystems for that matter), you should always backup you data first.

---

