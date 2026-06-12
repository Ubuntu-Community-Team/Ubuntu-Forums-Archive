---
title: "NTFS I think it's possible"
date: 2008-06-22
forum: General Help
---

### Post by ech0419 on 2008-06-22
Well, without a doubt I know someone else has posted this, but I personally need help with it.

I have 2 hard drives, both were exposed to a faulty power supply, at the moment I am trying to recover any data that I can off of the drives. One is *now** an unformatted 160GB volume and the other is a 320GB semi-working NTFS volume.
I would like to mount the NTFS volume and back-up what I can from it before it completely goes down the drain. If you could walk me through it that would be great. 

Sorry I had to post this but there may be more to it then just mounting it normally. 

**note* I'm not a super-noob I sort of know what I'm doing as long as you explain it to me. Also I'm a WinXp guy, sorry, but I'm certified with it.

---

### Post by Anlace on 2008-06-22
I've ran into this from time to time on drives that have been improperly shut down or removed (if external).

You can use "force" to mount the drive.  See this post: [http://ubuntuforums.org/showthread.php?t=836816&highlight=force+mount+ntfs+drive](http://ubuntuforums.org/showthread.php?t=836816&highlight=force+mount+ntfs+drive)

I understand that forcing a volume to mount can cause problems, however in my own experience where data may be lost irretrievably anyway the risk is acceptable.

Best of luck to you!

---

### Post by Happy_Man on 2008-06-22
Hm, first, plug in the drive. Does it get picked up by the computer and mount correctly? If so, wonderful. Start working. 

If not, then it's a bit harder, but by no means impossible. Open up a terminal (Applications --> Accessories --> Terminal) and enter ```
sudo fdisk -l
``` That will show you the device names of every volume visible to the computer. If your HDD shows up there, then enter ```
sudo mkdir /media/diskrecover
sudo mount /dev/sd?? <replace with the proper name> /media/diskrecover
``` and then start pulling data off. 

If none of that works, then there are very good data recovery softwares available for Linux. Two of them are detailed here: [http://ubuntuforums.org/showthread.php?t=417761](http://ubuntuforums.org/showthread.php?t=417761)

Hope this helps!

---

### Post by x1a4 on 2008-06-22
Hi,

get yourself root priviledges:
```
sudo -s
```

install the following packages: 

ntfs-3g
ntfs-config
ntfsdoc
ntfsprogs
libfuse2

create a mount point for the ntfs file system:
```
mkdir */mount/point*
```
where */mount/point* is the actual directory you're creating, of course.

mount the file system: 
```
mount -t [ntfs|ntfs-3g] -o defaults /dev/sdb1 /mount/point
```
where /dev/sdb1 is the device and partition.  sda1 is first partition on the first drive.  sda3 is the third partition on the first drive.  sdb1 is the first partition on the second drive.  and so on.

where [ntfs|ntfs-3g] is either **ntfs** or **ntfs-3g**.  Major difference between the two is that **ntfs-3g** provides write support.  If, however, all you need is to read the file system, use **ntfs**.

Now files on the partition are in /mount/point 

The ntfsprogs package has tools that will help you fix your ntfs partition.  Ensure the file system is unmounted first.

See the mount man page for more info on mounting file systems.

Good luck.

---

### Post by ech0419 on 2008-06-22
Thanks all of you, I didn't expect so many responces. 
*Happy_Man* yours was the simplest but it did not work. The drive did not mount but it gave me a couple other options about drive information. 

**Anlace* Well, I know there is data on the drive, If only I could get an explorer type program to access it. I don't want to ruin my chances completely. I'll look around at what the command does completely and give it a go. As of right now that looks like my best shot. I need to somehow boot my LiveCD from a flash drive with write support from my DVD Burner and slowly burn what I can (pictures preferably but anything usefull) onto a couple DVD's. 

**x1a4* Not to diss you completely but I'm running a LiveCD so installing packages is a pain. Not only that I'm limited to my 1GB of ram and my 1Gb flash drive in terms of space. If it comes down to it I will deffinitelly try it. 

Thanks all 3 of you, I have a long night fixing this ahead of me.

---

### Post by ech0419 on 2008-06-23
x1a4* I got pretty far, it's all good up to the ```
mount -t [ntfs|ntfs-3g] -o defaults /dev/sdb1 /mount/point
``` Where mount point is /Media/Disk it says "Mount: mount point /media/disk does not exist" I don't really know what to do if I cannot mount it, I have tried the same thing with "force" at the end but with the mount point non-existent what is the point? Any help on this would be great, I'm sending my entire tower down to OCZ for diagnostics and replacement since I believe all of this is the direct fault of a bad power supply. Ughh another 2 weeks of running a liveCD as a primary OS yay! not!

---

### Post by twbks on 2008-06-23
You need to make sure the directory /media/disk exists and is empty.  If it doesn't exist, you need to create it before attempting to mount the drive.
```
ls -ld /media/disk || mkdir -p /media/disk
```

---

### Post by ech0419 on 2008-06-23
twbks* That worked to an extent, after I typed that in and then tried to mount "/Media/Disk" It told me ```
"Mount: according to mtab, /dev/sda1 is already mounted on /media/disk"
``` It's definitely not mounted to the point were I can use it, any suggestions?

---

