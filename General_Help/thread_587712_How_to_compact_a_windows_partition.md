---
title: "How to compact a windows partition"
date: 2007-10-23
forum: General Help
---

### Post by jrharvey on 2007-10-23
Ok I recently tried to install ubuntu on my girlgriends laptop (both 7.04 and 7.10) and niether would let me resize the windows partition due to XP's stupid way of locationg system files at the begining and end. I tried to defrag numerous times and it will not comress. It only takes up about 20% of the drive and its rediculous that I can't resize it. I solved this problem with WUBI 7.04 and it worked like a charm. I would have to say this program rocks and I love the way it handles both OS's. Unfortunately this still uses the windows partition and as far as im concerned is not safe if she destroys her windows. I also REALLY want to use the new gutsy and just dont wanna wait till WUBI comes out on Hardy. Are there any options here??? Is there a program that will let me compact or compress my windows partition.

---

### Post by jrharvey on 2007-10-23
Also, as much as I want to she will not let me delete or reformat windows. She says that it must stay.

---

### Post by Shazaam on 2007-10-23
Try this with XP...
Open "System Restore", delete ALL but the LAST restore point.
Turn off the "Indexing Service".
Do a "Disk Cleanup" and clean out all of your browser(s) cache/temp files.
Disable the hard drive swap file (right-click My Computer>Properties>Advanced)
Reboot XP into "Safe Mode" and defrag.
Reboot into your Ubuntu Livecd and see if you can resize now.

As an aside, I have found that XP works fine if you have a partition TWICE the size of the used space ie 10gigs of used space = 20gig partition.
If you successfully resize XP and you are able to install Ubuntu don't forget to go back into XP and re-enable what you turned off.

---

### Post by anotherdisciple on 2007-10-23
I know that Vista (probably similar problems with XP) stores restore points, shadow copies, etc toward the center of the drive or partition, so the previous reply will help reduce this. When I did this it freed up some space, but not enough to do much good. I ended up reformatting the drive, making a partition that was only the space that I wanted Vista to have.

I have seen some scripts online that delete all of this extra junk in the middle of the drive, but I've never used one... and I"m not sure if it will screw up windows in any way. You could research it though... google it!

I'm on a transition out of Windows, but not many people are willing to do the same. If you can find a way to reinstall all the software, programs, etc. back on her computer, and if you can save all of her documents, pictures, music, etc... she can let you reformat and keep the same system. It will just be _less_ fragmented, and run better. Then she can play with Ubuntu and realize that she doesn't need Windows anymore... haha. I'd try to talk her into reformatting if you can't find a way to move all of those files.

---

### Post by jrharvey on 2007-10-23
Maybe one day she will let me delete windows :) I did get ubuntu 7.10 on ther by installing the WUBI 7.10 alpha. It works great even as an alpha. I did not have to repartition the drive.

---

