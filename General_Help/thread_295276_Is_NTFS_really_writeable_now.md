---
title: "Is NTFS really writeable now?"
date: 2006-11-07
forum: General Help
---

### Post by wsmoser2004 on 2006-11-07
I noticed in Kubuntu Edgy (maybe it was in Dapper too) that if I go to System Settings, click the "Advanced" tab, then click on "Devices and Filesystems", if I click on my Windows (NTFS) partition and click "Modify" it has a checkbox marked "Writeable".  Does this actually work?  And more importantly (to me), is it safe?  I was afraid to try it out myself...

---

### Post by ReaderRat on 2006-11-07
From what I have read, writing to NTFS is still in the experimental stage. You can, however, use a common FAT32 partition to write back and forth. There is also ext2fs available, but I don't know much about it. [**[color=RED]Here[/color]**](http://e2fsprogs.sourceforge.net/ext2.html) is a link to it.

---

### Post by Sef on 2006-11-07
> I noticed in Kubuntu Edgy (maybe it was in Dapper too) that if I go to System Settings, click the "Advanced" tab, then click on "Devices and Filesystems", if I click on my Windows (NTFS) partition and click "Modify" it has a checkbox marked "Writeable". Does this actually work? And more importantly (to me), is it safe? I was afraid to try it out myself...

It is not advisable to try it on your main computer.  The software is still beta, so bugs and crashes are to be expected.  If you have a spare computer, try it out on that.

---

### Post by givré on 2006-11-08
Some link if you want to try it. Many people use it daily without problems :
The driver home page : [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)
HowTo for ubuntu : [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

But the writable checkdbox for ntfs in kde is just a mistake i think. 
Write support is not yet build in edgy, even if packages are available in universe.

---

### Post by wsmoser2004 on 2006-11-08
OK, thanks for the ideas.  I do have the ext2fs driver in Windows, but it's just annoying whenever I'm in Kubuntu and I want to open a document saved on my NTFS partition and then save it back to the NTFS partition.  I'm going to look into the NTFS-3g idea...that might do what I'm looking for.

---

