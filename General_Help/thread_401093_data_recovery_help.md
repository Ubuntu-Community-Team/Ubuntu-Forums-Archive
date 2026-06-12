---
title: "data recovery help"
date: 2007-04-04
forum: General Help
---

### Post by AlexBryan on 2007-04-04
My idiot brother has managed to install Ubuntu over windows XP without saving his coursework. ](*,) As the Ubuntu install takes up only 2% of the drive I believe it's possible to view and recover the majority of the previous data from it, even if it was formatted. I've looked at a number of different data recovery software, but they seem to either be only for windows, or work on linux but only recover from linux partitions. The drive was formatted as NTFS before he installed ubuntu, but its ext3 now. So which format should he try to recover the data from, and if he needs to recover it from NTFS, which data recovery software works on linux and recovers NTFS data?

---

### Post by heimo on 2007-04-04
Hmm... I can reuse my previous post:

I'd try [autopsy]("http://packages.ubuntu.com/edgy/admin/autopsy"). Probably not going to be easy, if you're serious about recovering these files, stop using the disk now. You should probably boot from another disk / cd and do the work from there.

---

### Post by az on 2007-04-04
Foremost is a command-line tool which can recover files from a number of filesystems, including fat, ext3 and NTFS.  It can be installed and run from the live cd.

Boot from the live cd and then enable the universe repository and install foremost:

sudo apt-get install foremost

Assuming the lost files are on hda, you need to create a writeable directory on another drive where you can put the recovered files (lets say you have a big external usb drive (sdb)

sudo mount /dev/sdb1 /recovery
sudo mkdir /recovery/foremost

And then run foremost:
sudo foremost -i /dev/hda -o /recovery/foremost

The recovered files will then be owned by root.  Change their ownership so that you can use them:
sudo chown -R youruser:youruser /recovery/foremost

---

### Post by AlexBryan on 2007-04-04
OK thanks guys, I give those a try. Good idea about using the live CD, that hadn't occurred to me.

---

### Post by AlexBryan on 2007-04-04
Update: 
Seeing as autopsy is "not going to be easy" I thought I'd give foremost a try. From what I've read since your post, foremost searches the headers and footers of the raw data on the drive. Am I right in thinking the method you posted Az, will pretty much dump whats left on the drive to the destination folder? If so that would be **alot** of data and unfortunately my brother doesn't have another hard drive that size nor the funds to buy one. Do you know how, or know of a guide that explains how, to search for a certain file type i.e. .doc using foremost and dump all of those onto a usb pen drive?

---

### Post by az on 2007-04-04
You can specify which file types you want to recover using foremost.  By default (if you don't specify a type) it will recover all file types.

sudo foremost -i /dev/hda -o /recovery/foremost -t ole

(you can specify .doc, but ole will grab all of the following: PowerPoint, Word, Excel, Access, and Star-Writer)
[http://foremost.sourceforge.net/foremost.html](http://foremost.sourceforge.net/foremost.html)

---

### Post by aysiu on 2007-04-04
If the NTFS drive was entirely reformatted as Ext3, I don't believe you'll be able to recover the data.

If, however, the NTFS partition was simply resized to make room for the Ext3 partition, then you can easily get stuff off the NTFS partition by mounting it:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by AlexBryan on 2007-04-04
Hi again. I'm trying to do this bit:

sudo mount /dev/sda1 /recovery
sudo mkdir /recovery/foremost

(sda1 is a usb flash drive) 

and it keeps bringing up the error 'mount: mount point /recovery does not exist.' What am I doing wrong?

---

### Post by aysiu on 2007-04-04
Because you didn't create /recovery, I guess. ```
sudo mkdir /recovery
sudo mount /dev/sda1 /recovery
```

---

### Post by AlexBryan on 2007-04-04
Thanks for the help everyone. Unfortunately Aysiu was correct in thinking it wouldn't work as the NTFS partition was completely reformatted as EXT3.

---

### Post by az on 2007-04-04
> **AlexBryan said:**
> Thanks for the help everyone. Unfortunately Aysiu was correct in thinking it wouldn't work as the NTFS partition was completely reformatted as EXT3.

Formatting to ext3 does not overwrite a lot of data.  You lose about one or two percent of your recoverable data, nothing more.  It's not like every block is zeroed; not at all.

I took a usb pen drive which was formatted to fat32 and turned it into etx3.  Without writing any files to it, I was able to recover more files than what was on it before I played with it - I recoverd files I had deleted several months before.  Most of the files were jpegs and I was able to determine that very few (only one) was corrupt.

If your brother only installed Ubuntu and did not fill the disk with files, most of your data should still be there.

---

### Post by AlexBryan on 2007-04-04
We did as you said and searched for ole and at the end of the process the folder created was empty so I figured all the files had been lost.

---

### Post by az on 2007-04-05
Try using the -w switch (audit mode) with no file type.  That will just tell you what files it can recover without actually saving them.

---

### Post by ubu-for on 2007-04-05
> **AlexBryan said:**
> My idiot brother has managed to install Ubuntu over windows XP without saving his coursework. ](*,) As the Ubuntu install takes up only 2% of the drive I believe it's possible to view and recover the majority of the previous data from it, even if it was formatted. I've looked at a number of different data recovery software, but they seem to either be only for windows, or work on linux but only recover from linux partitions. The drive was formatted as NTFS before he installed ubuntu, but its ext3 now. So which format should he try to recover the data from, and if he needs to recover it from NTFS, which data recovery software works on linux and recovers NTFS data?

You can try the following software, but install them only on a different hard disk!

[Acronis Disk Director Suite 10.0 Trial](http://eu.acronis.com/homecomputing/download/link/?DiskDirectorSuite10.0_d_en.exe) (Windows)

[R-Linux](http://www.r-tt.com/downloads/rlinux_en_10.exe) (Windows)

[PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) (OS independent)

[TestDisk](http://www.cgsecurity.org/wiki/TestDisk) (OS independent)

---

