---
title: "fat32 -&gt; all files gone after Winblows accessed drive"
date: 2006-10-09
forum: General Help
---

### Post by harty83 on 2006-10-09
Okay so I have a fat32 partition that I use to store shared files between winblows and ubuntu.  Originally, in Ubuntu all my files showed up fine but would not show up in Winblows.  So under winblows, I created a folder just to see if it would show up in ubuntu which it didn't (I could still see all my other files in ubuntu at this point).  But after rebooting again, all my files are gone!!  Only winblows Recycled and System Volume Information folders show up.  Well, when I look at the partition through gparted, it says that 802.80 megabytes are taken up.  That tells me my files are still there somewhere!  How can I recover them?  Ubuntu, knoppix, nor winblows will show the files.

They are important files!!  I would really appreciate any help!
Thanks in advance!
Alan

---

### Post by anaconda on 2006-10-09
Do you have winblows 2000 ? It has sometimes problems with fat32 partitions that are bigger than 32GB   

Sorry cant reaaly help.. just wanted to ask..

---

### Post by harty83 on 2006-10-09
No, I have xp pro and the partition is only 10gb

---

### Post by harty83 on 2006-10-09
Sigh...I had to give up everything.  I used some file recovery programs through winblows and was able to find everything but the files I really needed.  So, I just ended up reformatting the partition and now both ubuntu and windows recognizes it properly.  

Does anyone know what might have caused this so I can avoid it in the future?

---

