---
title: "Share external USB drive via SAMBA?"
date: 2007-01-05
forum: General Help
---

### Post by kirkm76 on 2007-01-05
Ok, here's the deal.  I have been a windows guy with a little bit of unix for 10+ years.  I decided to go ahead and learn linux so I set as a goal for my first project to migrate my home mp3 server to Linux.  

I have gotten the machine (dell PIII laptop) running and gotten samba set up.  I can share files and directories that are on my hard drive and see them on my windows xp box.  Problem is that my music collection is on a 300 gig usb drive.  I can create shares and see them on the windows box, but can't access them.  If I try to change permissions on the drive it says it's a read only file system.  

This may very well be something simple, or it may just not work.  Any help or guidance would be appreciated.

---

### Post by PilotJLR on 2007-01-05
What filesystem does your usb hard disk use??

If it's NTFS, then that is read-only in linux, unless you install the unstable read/write NTFS driver.

---

### Post by kirkm76 on 2007-01-06
then that's the problem...thanks.  I hadn't checked...I thought it was FAT32.

---

### Post by dgray_from_dc on 2007-01-11
I had a number of problems (mainly write permissions) even with FAT32.  What I ended up doing was getting a second drive of equal size (250GB), and formatting it ext3 and migrating.  The problem with using NTFS or FAT32 with Linux is that you don't get the file permissions offered by filesystems like ext2/3 of ReiserFS that Linux has support for natively.  I created an MP3/Video/Application/...  (let's just say general purpose) server.  Everything became infinitely easier to deal with once I was dealing with an ext3 drive.  I now plan on taking my original drive and starting a 500GB Linear Mode Software RAID array when I have the time.

---

### Post by squinter on 2008-04-06
Interesting, so ...

I have a Ubuntu machine that I'm using as a server. On that machine I attached a 500GB external USB drive. If I reformat that drive to ext3 (or other linux format). And if I share it on the network. Would Windows machines be able to access the files in the drive, even though it is ext3?

At the moment I think it is FAT32 and I can't seem to set up file permission (chmod). I'm wondering if it is because FAT32, or I didn't set it up correctly. I could see the shared drive from another computer, but for read-only.

Please help me :-|

---

### Post by dgray_from_dc on 2008-04-08
As in my previous post, FAT32 doesn't have permissions built in.

Sometimes files can be accessed locally with a FAT32 disk, but I have found that over a network share, getting controlled read/write access can be difficult to impossible.

Converting to a Linux native file system will definitely help this.

Once done, basic sharing over samba is easy and with a little work, it can be customized into a fairly complex file server system.

---

### Post by dcstar on 2008-04-08
> **squinter said:**
> 
.........
At the moment I think it is FAT32 and I can't seem to set up file permission (chmod). I'm wondering if it is because FAT32, or I didn't set it up correctly. I could see the shared drive from another computer, but for read-only.

Please help me :-|

There are two levels of permissions in file sharing - there is the "Share" permissions and then the underlying native filesystem permissions.

You can have a folder with RW permissions, but if you access it via a share with RO permissions, then you can only read from it.

Same goes the other way around, if you want RW permission then the share **and** the native filesystem must **both** have appropriate RW set and working.

"Share" permissions are set in your samba.conf file, the native filesystem permissions are an issue for the account credentials accessing the share.

---

