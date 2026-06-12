---
title: "Advised filesytem for external backup harddrive"
date: 2008-03-10
forum: General Help
---

### Post by MrZehl on 2008-03-10
Today is my lucky day. Yesterday my ext3 partition with all my important data crashed and today something incredible happened, it suddenly worked again. Well... if that isn't a message of 'You should backup your stuff.

So I bought an external 500Gb Lacie hd nad want to use it as backup drive. Standard it is FAT32. I never had problems with fat32, but it is not really safe for what I understand.

What is the best filesystem for backuip my important data? I don't care if Windows can read the drive. It is only for backup and therefore I can use any Linux livecd. Mostly I work with my Ubuntu machine anyway. 

So what is the most secure recoverable stable filesystem? I know... a harddisk backup isn't real backup anyway. The most important data I should backup on DVD and store them in different places.   But I'm not gonna burn hundreds of DVD's. Performance is not an issue. I just wanna be safe.

Ext3? Reiserfs? Any Other? And why?

---

### Post by monte48lowes on 2008-03-10
I use ext3 on my external disc. There is a windows driver available to read ext3 drives.

Mike

---

### Post by phrawzty on 2008-03-10
> **MrZehl said:**
> What is the best filesystem for backuip my important data? I don't care if Windows can read the drive. It is only for backup and therefore I can use any Linux livecd. Mostly I work with my Ubuntu machine anyway. 

So what is the most secure recoverable stable filesystem?

From what you've indicated, your only real requirement is a journaling filesystem :
[http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)

Generally speaking, you have four options : ext3, reiser, jfs, and xfs.  Realistically speaking, reiser and ext3 are your obvious choices.  Both work, and while they are technically very different, from a user perspective the only difference between the two is popularity : ext3 is much, much more widely used.

---

### Post by der_joachim on 2008-03-10
If you want to be able to view your disk from windows: +1 for ext3. [Here's the driver]("http://www.fs-driver.org/"). It can read ext3 as well.

---

### Post by defishguy on 2008-03-10
I would recommend avoiding FAT32 if you are going to be archiving the backup in a single tarball.  Fat32 has an 4GB file size limit... anything larger than that and the tarball will be corrupt.

---

### Post by monte48lowes on 2008-03-10
[http://www.mikerubel.org/computers/rsync_snapshots/]("http://www.mikerubel.org/computers/rsync_snapshots/")

This is the website I used to write a backup script to backup my /home directory every day. Very useful.

Mike

---

### Post by articpenguin on 2008-03-10
also avoid ext2 as that isnt journalled.

reiserfs corrupts way to easy so does xfs.

---

### Post by MrZehl on 2008-03-12
Thank you all. ext3 it is.

---

