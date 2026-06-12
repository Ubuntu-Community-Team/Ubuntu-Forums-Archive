---
title: "External Hard Drive.. Which format?"
date: 2006-11-30
forum: General Help
---

### Post by Kdar on 2006-11-30
I got new external HD not long time ago.

And I plan to use it in Windows and in Linux.

So. How should I format it.. so it would work with Linux and Windows?

---

### Post by taurus on 2006-11-30
You want to format it with fat32 filesystem.  You can do that directly in Ubuntu.  Just install gparted and use it to format your new harddrive then.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install gparted
```
It will be in System -> Administration.

---

### Post by ser1alsn1per on 2006-11-30
you might need to edit the fstab file to auto mount it

---

### Post by timcredible on 2006-11-30
you shouldn't have to touch the fstab - it should auto-mount when connected.

be aware that there are no user permissions with fat32, so you might consider splitting the hd into 2 partitions - one for fat32 for using with windows, and ext3 or reiserfs on the other partition for linux.  it's easy to do with gparted or qtparted and works fine - the drive should automount both partitions when connected (does for my 100gb external drive).

---

### Post by taurus on 2006-11-30
> **timcredible said:**
> you shouldn't have to touch the fstab - it should auto-mount when connected.

be aware that there are no user permissions with fat32, so you might consider splitting the hd into 2 partitions - one for fat32 for using with windows, and ext3 or reiserfs on the other partition for linux.  it's easy to do with gparted or qtparted and works fine - the drive should automount both partitions when connected (does for my 100gb external drive).

Anybody can write to fat32 if you mount it with "umask=000"!!!  :rolleyes:

---

### Post by newagelink on 2006-12-01
It's not possible to change the format of a hard drive without losing all data stored on it, is it?

---

### Post by AusIV4 on 2006-12-01
> **newagelink said:**
> It's not possible to change the format of a hard drive without losing all data stored on it, is it?
Nope. If you must keep it, you'll need to back everything up before reformatting.

To the original question of what FS to use, I faced the same problem about a month ago. NTFS isn't reliable on Linux, FAT32 won't allow files larger than 4GB. Since I'm doing backups, I needed files larger than 4GB. I settled on Ext3 and used [this drive]("http://www.fs-driver.org/") to allow my Windows box to read the device. I've found this to be the best solution to that problem.

If you need to be able to take it to other places where you can't install a new driver, FAT32 is the best you can do.

---

### Post by scrook on 2006-12-01
You can also use the EXT 2/3 driver for windows found here:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

I've been using it for months on my windows install with no problems.

---

### Post by strabes on 2006-12-02
I would STRONGLY recommend you do what scrook said. I have also been using it for a long time with no problems. It is really great. The only problem with using it with an external HD is that if it you want to take it somewhere and use it with a windows comp you would have to install fs-driver to use it which might be a problem on a public computer.

---

### Post by techflat on 2006-12-13
Hi there

I've been using the driver from [http://www.fs-driver.org/](http://www.fs-driver.org/) for a while now, the only difference is that I have it for an internal device.

I'm planing to travel with an external HD so here's what I'm going to do:

1 - Divide HD into 2 partitions, one small (=1GB) and the other one big (=70GB or so)
2 - Small partition is going to be FAT32 and big partition is going to be ext3
3 - On the big ext3 partition, I'm planing to put my data files
4 - On the small fat32 I'm going to put essential data files + the drivers from [http://www.fs-driver.org/](http://www.fs-driver.org/)

So, If I need to use my large partition on a Windows machine, I just have to make the small partition visible from Windows and then install the driver. If I need to use the large partition on Linux I just have to mount it, it's the same with the small partition.

To partition and format the HD external drive, I use gparted. I've used qtparted too but I prefer gparted.

I don't know if this is true, but apparently, when moving or copying files from an ext3 to a FAT32, capital letters are made small letters (hope you understand what I mean, from A to a, or B to b). Can someone confirm this?

Cheers

---

### Post by scrook on 2006-12-13
While I haven't tested this, it makes sense since FAT32 is not case sensitive. So say you have a file named 'Textfile.txt' on a FAT32 partition, you could not make another file called 'TEXTFILE.txt' since the FS doesn't see the difference between them.

Also if you are planning on taking the external drive between machines you may want to google for a program called Explore2FS in addition to the EXT2/3 file system drivers. It is a stand alone executable which is useful if you are mounting your drive on a machine where you can't or don't want to install drivers.

scott

---

### Post by mcduck on 2006-12-13
No, at least for me the file names don't change when copying to FAT32.

I have my 100GB external disk partitioned to 90GB EXT3 and 10GB FAT32 so I can still easily use it with macs and windows machines.

---

### Post by techflat on 2006-12-13
Thanx for the info.


techflat

---

### Post by techflat on 2006-12-13
> **mcduck said:**
> No, at least for me the file names don't change when copying to FAT32.

I have my 100GB external disk partitioned to 90GB EXT3 and 10GB FAT32 so I can still easily use it with macs and windows machines.

Have you tried copying 2 different files with the same "overall" name in the same directory. Like text.txt and TEXT.TXT. I don't know if that works.

You mentioned mac, I'm thinking about getting one, I'm guessing it can mount ext3 and FAT32 sinces OSX is BSD like. Am I right?

---

### Post by mcduck on 2006-12-14
> **techflat said:**
> Have you tried copying 2 different files with the same "overall" name in the same directory. Like text.txt and TEXT.TXT. I don't know if that works.

You mentioned mac, I'm thinking about getting one, I'm guessing it can mount ext3 and FAT32 sinces OSX is BSD like. Am I right?
I just tried, and I was able to copy both 'Text File.txt' and 'text file.txt' to the same directory. I think that it depends on the character set you are using. (I'm not sure though..)

Mac's don't read ext3, at least not out-of-the-box.

---

### Post by jlempen on 2006-12-14
If you need to work on Linux, Windows and OSX and frequently work with files larger than 4 gigs, your best solution is OSX's HFS+ file system. You'll have read-write access in Ubuntu and (obviously) in OSX. Then get Mediafour's MacDrive software to be able to mount the partition on Windows. Works like a charm even with very large 20 gig video files.

As for the capitals problem on FAT32 partitions, i can confirm this happens to me as well. Even when I copy files from one FAT32 drive to another in Ubuntu. Most annoying...


Hope it helps,

J.

---

### Post by fakie_flip on 2007-03-04
If I am running Linux in a raid 1 (mirrored) configuration, then how can I use the fs-driver? Would that cause problems?

---

### Post by Xeor on 2007-06-25
Would it not be better to partition the hard drive as follows?

3Gig in FAT32
117Gig in Ext2 (rather than Ext3)

I believe Ext2 is more Windows compatible than Ext3.
FAT32 for putting essential files such as "Ext2IFS_1_10c.exe" to make it possible for Windows to read/write Ext2 in a quick and easy way or quick way to get Windows files from a computer without having to install Ext2FIS when not possible for example.

And NTFS on Linux can get lost for being as compatible as Ext3 on Windows.

What would be the disadvantages doing it this way?

---

