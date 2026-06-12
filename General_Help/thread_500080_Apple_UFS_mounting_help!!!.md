---
title: "Apple UFS mounting help!!!"
date: 2007-07-13
forum: General Help
---

### Post by elmo541992 on 2007-07-13
I had some files on my old mac (osx) but then it died.  So I'm trying to recover the files from the hfs+ drive (mainly pics), But its in my my docs folder under my user name, so therfor i cant access the files unless im using osx.  so i go to my friends house, and use his mac to transfer files from the old hd to a spare hd formated in apple ufs.  i figure, hey it unix!!! good ol bubtu should be able to read this... but it cant mount it...;( i tried Google, but it didnt really help.  so if someone could tell me how to mount apple ufs, that would be awesome!!!

---

### Post by thully on 2007-07-13
Try, at the command line:

sudo mount -t ufs /dev/<device> -o ro /mnt

(substitute the HD's device node (probably sdb1 or sdb2) for <device>

Then, it should mount in /mnt.  I think this is the right syntax, but I can't test it now...
Anyway, the reason UFS won't mount automatically is that it insists on read-only.  

Just as a side note: despite UFS being "UNIX", Linux actually doesn't support it very well at all.  When sharing data, you're better off using HFS+ (Mac OS Extended in Apple-speak).  Linux reads that just fine and can write non-journaled HFS+ drives (journaling can be enabled/disabled in Disk Utility on OS X).  There is even a case-sensitive HFS+, which I actually used to share the same home partition between OS X/Linux on my MacBook...

---

### Post by elmo541992 on 2007-07-13
it kinda works...  it looks like it mounts, but when i goto /mnt, it says "Sorry, ctsldn't display all the contents of "mnt"." then if gives me an empty mnt folder.  also, the hd used to be listed on  the places side bar, but it isn't now. any thoughts???

i don't know if this will make a difference, but im using 64-bit feisty. Thanks for your help!!!

---

### Post by thully on 2007-07-13
All I can say is try reformatting the drive as HFS+ next time - I figure you can't really do much with UFS in Linux.  BSD can, though, so you may be able to use a BSD live cd and copy the contents off the HD to a Linux partition that way...

---

