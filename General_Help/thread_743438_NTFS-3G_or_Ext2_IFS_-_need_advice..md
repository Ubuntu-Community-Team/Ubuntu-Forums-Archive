---
title: "NTFS-3G or Ext2 IFS - need advice."
date: 2008-04-02
forum: General Help
---

### Post by pillypoon on 2008-04-02
Hello ,

Im having a hard time deciding which file system I should use to share my media files with XP and Linux. I have a 500gb drive that I will be using for MP3s and movie files.  Should I go with NTFS and use the ntfs-3g in linux or should I use EXT3 and use ext2IFS in windows?  :)  What would be the more reliable choice? Which one would have the least problems.  I was even thinking of using a fat32 partition for just the mp3s.    What do you think? 

Please help me decide!  :)

TIA,
Pilly  :guitar:

---

### Post by bwhite82 on 2008-04-02
Fat32

Edit: For BOTH. This will give you the least amount of headaches.

---

### Post by anaconda on 2008-04-02
If you use linux more than windows then ext3
and
if you use windows more then ntfs

I would forget fat, because there is the annoying 4GB file size limit AND fat doesn't have permissions and so every file is assumed to be executables in linux.. so if you for example doubleclick a .txt file ubuntu  will ask if you want to execute the file or open it...
Dont know if the same happens with .mp3:s (propably not..

---

### Post by bwhite82 on 2008-04-02
Fat32 works good for me w/ movies and mp3s (no permissions problems). I have neither that are over 4gb however, if you do, I would recommend ext3 as well.

---

### Post by pillypoon on 2008-04-03
Thanks for your feedback.

I did notice something funny when using Ext3 in XP.   I made a backup copy of my friends wedding DVD using DVDShrink.  I told DVDshrink to convert the image into an .ISO onto my Ext3 partition. Instead of converting it into an ISO it converted it into multiple files.  It burned and works fine but im wondering if thats a bug in the ext2 IFS program or DVDShink.  Any ideas?

---

