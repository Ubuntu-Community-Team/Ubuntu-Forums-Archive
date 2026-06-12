---
title: "[SOLVED] sdb1 is 82.6% non-contiguous!!!!!!! Why??"
date: 2008-02-15
forum: General Help
---

### Post by jesushero on 2008-02-15
My installation of Ubuntu Studio with the rt kernel is less than six months old. fsck returns a 6% non-contiguous on sda1 which is a western digital 500gb ata drive mounted as / (root) and 82.6% non-contiguous on sdb1 which is a western digital 120gb ata drive. sda1 is 48% full while sdb1 is 9% full!!!!!! So with only a 9% usage, can anybody explain why this is happening???? What should I do about it?? Generally, if I have a large percentage of non-contiguous space, is there a defragment program or is it time to re-install??? If the answer is to re-install, I must admit I am sooooooo greatly disappointed by Linux!! 

PS: sdc1 is my swap partition, a whole western digital 20gb ata drive. Could the excessive swap size affect the system in any negative way?? I just didn't need it as anything else and decided to use it all for swap. I've got 512mb of ram and during heavy audio and video processing use I've seen the swap usage being about 3gb. Usually it's about the 20-30 mb.

Any ideas?????? I'm getting a bit worried!!

---

### Post by accatagon on 2008-02-15
I honestly have absolutely no idea why your hard drive is so jumbled, but honestly, unless there is some reason to suspect that the hard drive is failing or it's causing a major slow down, I wouldn't worry about it too much. Really the only time it would be a problem is if your hard drive failed completely and you needed to recover data from it. In general though, most operating systems (Windows, Mac, and Linux) aren't actually affected that much by fragmentation. This is probably why the NTFS file system doesn't normally resist fragmentation, but that's just idle speculation on my part. The kernel is actually designed to put all hard disk requests in roughly sequential order before sending them. The assumption is that on a modern hard disk you're going to get requests that are all over the place anyway, no matter how contiguous each individual file is (any program may request thousands of files just to start-up). Even with windows, which is supposed to be horrid as far as becoming fragmented, as far as I know (I could be wrong) defragmenting yields at best marginal performance gains. 

That said. . . if you have noticed a major hit in performance, there might be cause for concern. Otherwise, I'd kind of like to know what the other partition was mounted as. For example, it seems like /var or /tmp would be MUCH more likely to become fragmented, since there is a lot of appending files and whatnot going on. Also, if it's a FAT32 or NTFS partition, it would be more likely to become fragmented. 

But overall, unless there is some special consideration like a loss of performance or an absolute need to have files contiguous, I wouldn't worry about it. You can check other data about the hard drive's health using "smartctl --all /dev/sdb" after downloading the smartmontools package, but honestly I just really wouldn't worry too much.

That said, if there are any other considerations or if you would like to give me more detalis about this second hard drive so that I can try to figure out what's going on, feel free to do so.  

Also, I really really doubt it's your swap partition's fault.

---

### Post by jesushero on 2008-02-16
Hey, thanks for replying! So, sdb is primary slave, ext3 filesystem, formatted less than 3 months ago (from NTFS as it was being used in a windows system before). It is mounted to /home/bkp which is not a user directory, it is just a directory I created in the home folder and I use mainly for backup purposes. This being said, I do not often use this drive! It just sits there, and from time to time I put on some video file or copy some backup data-DVD on it and then remove it again. At the moment it only has some audio and video files on.  

I downloaded the smartmontools and ran the smartctl which returned no errors. I also did the short test, no errors there, but it returned the alarming lifetime of 1438 hours which is less than 60 days!!!!!!!! Is this like, accurate???? Should I take this seriously and just remove everything from it?? 60 days is not much of a lifetime expectance, especially considering that my computer usually stays on for several days or even weeks in a row as it is running servers. 

Also, since you mentioned that, I have not specified any /var or /tmp partitions, so I guess these are mounted on the root filesystem on sda1. 

Of course, I have not noticed any decline in performance since I do not often use this drive, and when I do it is unattended (I just leave something copying on it and get on with my work elsewhere). 

So the percentage that fsck returns will always go up until it reaches 100%?? Then what?? Is it not reversible in any way?

---

### Post by vanadium on 2008-02-16
Is it possible that you mainly have very large files on your sdb1? I presume that large audio files that are regularly edited or copied/deleted might inevitably acquire some fragmentation oven on disks with plenty of free space. However, I guess that in these conditions the non-contiguous pieces would all be large anyway, which means that for practical purposes, it would not cause any significant degradation in performance. Briefly, I would not worry about that.

---

### Post by jesushero on 2008-02-16
Could be, if around 800mb per file can be considered large nowadays. I surely hope it is not something to worry about. Thank you for your replies anyway!!

---

### Post by vanadium on 2008-02-17
800 mb files are large files, even nowadays, and performance would not be hit if that file was stored in say four different chunks of 200 mb.

---

### Post by jesushero on 2008-02-18
Ok, thanks for replying. 

Once a drive gets clogged up, what do I do to restore it? Format it? Or will ext3 work on it on its own?

---

### Post by vanadium on 2008-02-18
For a drive that is quite full and seriously fragmented, backing up the data and restoring them will surely do the trick. I guess that deleting and copying back would be sufficient, and that reformatting woudn't be necessary but I could be wrong. Fact is that reformatting might just be quicker thus more convenient than deleting all the files.

---

### Post by jesushero on 2008-02-18
Ok, thank you!! I will probably transfer everything to the other drive and try to restore this one.. So, Solved, I guess! Thanks!!

---

