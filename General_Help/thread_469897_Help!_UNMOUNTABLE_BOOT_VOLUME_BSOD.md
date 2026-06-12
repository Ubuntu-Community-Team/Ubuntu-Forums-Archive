---
title: "Help! UNMOUNTABLE_BOOT_VOLUME BSOD"
date: 2007-06-10
forum: General Help
---

### Post by tahnok on 2007-06-10
I recently installed 7.04 on my dell 6400. I had to do some resizing of partitions to make room for ubuntu. The installation was completed with no errors. Linux boots fine and I can see both of my NTFS partitions (I have 2 one for windows and one for all of my files). The only problem is when I try and boot Windows it gives me an UNMOUNTABLE_BOOT_VOLUME BSOD. Is there any way to fix it? I've been searching through the forums for answers, but no one seems to be able to solve it. I've got all of my data backed up, but I'd like to know how to fix this and how to avoid it in the future (this happened once before). At the very least if I can learn what I screwed up I'll be happy.
Thanks in advance.

---

### Post by Shazaam on 2007-06-10
Did you do a defrag in Windows before a resize?
Some links for you...
[http://support.microsoft.com/kb/297185](http://support.microsoft.com/kb/297185)
[http://www.daniweb.com/techtalkforums/thread41835.html](http://www.daniweb.com/techtalkforums/thread41835.html)

---

### Post by tpg on 2007-06-10
Could it be that boot.ini on your windows partition is now pointing to the wrong place for the windows disk, so it's actually trying to mount your linux partition?

If you can find a way to edit boot.ini (you'll need ntfs-3g installed to be able to write to an ntfs partition), you could try fiddling the partition numbers around and see if you get anywhere. 

Or maybe you could use a Windows disk in system repair mode, or whatever it is they call it. You know, where you boot the CD and get yourself into a DOS prompt. From there, you could edit stuff on the ntfs partition without any problems.

---

### Post by tahnok on 2007-06-10
To Shazaam:
No I hadn't, but I had installed windows 3 days ago so I figured it wouldn't be fragmented. I guess I should have.

To  tpg: I've tried using the windows recovery console. I tried chkdsk, chkdsk /P, chkdsk /R and they didn't work they just told me this volume contains one or more unrecoverable errors. I will try messing with the boot.ini file. 

BTW is there a good ghost like program for ubuntu? If I have to wipe my drive I don't want to have to reinstall ubuntu b/c I got Beryl working (woot!)

---

### Post by tahnok on 2007-06-13
bump

---

### Post by Shazaam on 2007-06-13
In the section labeled "Damaged FileSystem" did you follow the directions about "fixboot"?

Yes there is it's called Partimage. I haven't used it but others swear by it.

---

### Post by tahnok on 2007-06-13
Yes I did, but it didn't help. I've just reinstalled everything. Hopefully this never happens again.
BTW thanks for your help.

---

