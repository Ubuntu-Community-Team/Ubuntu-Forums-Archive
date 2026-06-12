---
title: "What file system should I use?"
date: 2008-04-28
forum: General Help
---

### Post by patrickaupperle on 2008-04-28
I just bought an external hard drive and don't know which file system to use. I use Linux on my main computer, but Windows read and write capability is definitely a plus. What do you think I should use for the file system?

---

### Post by kerry_s on 2008-04-28
just leave the fat format, linux and windows both can use it.

---

### Post by retrow on 2008-04-28
If you want both Ubuntu and Windows to read/write that drive, go with NTFS. Don't go with FAT32 since it tends to get fragmented easily and can't hold files larger than 4GB.

---

### Post by patrickaupperle on 2008-04-28
> **retrow said:**
> If you want both Ubuntu and Windows to read/write that drive, go with NTFS. Don't go with FAT32 since it tends to get fragmented easily and can't hold files larger than 4GB.

Doesn't ntfs fragment also? Can I defrag from linux?

---

### Post by seamuso on 2008-04-28
you can use ext3 and install this .. [http://www.fs-driver.org/](http://www.fs-driver.org/) in windows to get access to your linux drives. It really depends on where you're going ot be using the drive more frequently.

---

### Post by patrickaupperle on 2008-04-28
> **seamuso said:**
> you can use ext3 and install this .. [http://www.fs-driver.org/](http://www.fs-driver.org/) in windows to get access to your linux drives. It really depends on where you're going ot be using the drive more frequently.

OK. I think I will use ext3.

---

### Post by retrow on 2008-04-28
NTFS fragments much slower than FAT systems because of the way files are written. NTFS leaves some space between files when they are written so that if you modify them you still have space before and after it to keep it continuous. In Linux practically all filesystems function that way.

Unfortunately you can't 'defrafment' with Linux. However you can fsck the drive once in a while to keep up the performance.

---

### Post by patrickaupperle on 2008-04-28
Ok, so I heard that ext3 is technically supperior. Is this true? What advantages do each have? Which should I use?

---

### Post by retrow on 2008-04-28
Yes, ext3 is more superior because of the way Linux preallocates a larger block for frequently used files. SO fragmentation in ext3 is slower than fragmentation in NTFS.

The possible reason why you might want to choose NTFS would be if you plan to carry your external drive with you to different place where people would prohibit you from installing ext3 driver 'only' to read from your drive.

---

### Post by elmer_42 on 2008-04-28
Personally, I would use NTFS over ext3. Yes, ext3 doesn't really fragment, but it can not be read by default in Windows. The biggest advantage of an external hard drive is that it is portable. You can take it anywhere! The problem is that most people don't have the ability to read ext3. That's where NTFS comes in, because Windows can read it by default. Also, I hate FAT32 because you can't store files over 4GiB, which is unacceptable for me.

---

### Post by evozniak on 2008-04-28
in my opinion NTFS is the best choice
you can read and write in linux and linux and setup is easer, dont need any driver.

EXT3 in windows is very experimental and instable at this time.

---

### Post by seamuso on 2008-04-28
> **evozniak said:**
> in my opinion NTFS is the best choice
you can read and write in linux and linux and setup is easer, dont need any driver.

EXT3 in windows is very experimental and instable at this time.

It still depends on where the disk will be used more frequently. If it's a removable drive that is used more in a windows envirinment, then NTFS is a great choice, if the main system is linux, it's still better to use a filesystem that's native to linux.

For instance, I have a few flash drives, some I use only in linux .. they are formatted ext3 .. the others are formatted ntfs/fat32 so I can transport files needed for repairs on clients' computers. The need really justifies the solution.

I've been using the driver that I linked to since the pre-RC days in vista and for about the same amount of time in xp with no issues.

---

### Post by patrickaupperle on 2008-04-28
Ok, I will use ntfs. I do have a windows computer to defrag with when needed. Also my public library has a really fast internet connection to dl isos with.

---

