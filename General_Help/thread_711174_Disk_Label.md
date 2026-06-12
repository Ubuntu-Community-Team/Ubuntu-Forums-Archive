---
title: "Disk Label"
date: 2008-02-29
forum: General Help
---

### Post by PsiBer on 2008-02-29
I hope this will help others with minor Disk Label issues similar to mine:

I resized a FAT32 to make a temp back-up of some linux stuff in case something went horrible wrong (it didn't everything was fine) and when I was finnished and removed the back-up part and resized the fat32 part back to its former glory, my Ubuntu 7.1 forgot the FAT32 label... I was a little vexed by this... having spy'd around the contents of my /dev folder not so long ago to solve a UUID related Boot problem I knew there was a directory called by-label in there somewhere, sure enough the label under /dev/disk/by-label was missing, I did boot into Win to make sure the part still had the correct label and that 7.1 had just forgoten what it was, and that was the case, I moved on to see if I could just add the new label to by-label so I:
sudo nautilus
and copy'd the correct link from by-id and paste'd it to by-label and renamed it to what I wanted the new label (same as in Win BTW) in all caps, re-started and poof! it was back! instead of calling it Disk-1 (as before this fix) after automounting all my drives after log-in it had the new label I didn't have to change fstab or anything!

---

### Post by santaslittlehelper on 2008-02-29
Hi

Maybe mark it as solved then. ;)

---

