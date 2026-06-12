---
title: "Installed linux on wrong partition"
date: 2007-06-05
forum: General Help
---

### Post by snipes23 on 2007-06-05
I somehow overwrote over xp, and now my Ubuntu 7.04 is on Partition1, Instead of being on Partition 2.  This is how I wanted to set it up:

Partition1 -ntfs - Windows Xp
Partition2 -ext3 - Ubuntu 7.04
Partition 3 -swap

But This is what it says when I put Xp disc in at the partition part

c: Partition1 <Inactive  OS/2 Boot Man> 132,183mb, 180,653mb used  (assuming ubuntu is on here)
e: Partiton2 19061mb, 19061 free
f: Partition3 879mb, 878mb free

Now is there a way I can resize c: Partition1 and make it smaller, Add to Partition2 and change to ntfs to Install Xp,  And what am I supposed to do with swap exactly?  I was also thinking of adding another partition for  home partition "/home" ext3.  If I have to Redo everything I will, I'm just glad I've got Ubuntu running after 3 days of trying to figure out graphic problems due to ati X1800.  

Hopefully this makes sense, any help appreciated.  Mike

---

### Post by mikewhatever on 2007-06-05
Since you have to redo the partitions (ntfs, /home) and probably know how to fix the problems with the graphics card, I'd suggest starting with the clean installation of Windows on the first partition of the desired size, overwriting Ubuntu and leaving the rest of the space unallocated. That done, you can set up the partitions you need for Ubuntu and install it ones again.

---

### Post by snipes23 on 2007-06-05
I think the only problem I might have is doing the same thing again on accident.  Should I do it like this

Install XP, reboot, Install Ubuntu, do all of the partition in Ubuntu ( making the ntfs  smaller in Ubuntu via slider), then I think manually adding partitions /root, /home, and swap as ext3.  Is there an option of what to Install Ubuntu too? and if so, Do I add to /root or the swap? thanks for the help, Mike

---

### Post by mikewhatever on 2007-06-05
As suggested above, you can install Windows on the first partition of the desired size, leaving the rest of the space unallocated. Then, partition the unallocated space, skipping the resizing stage. It is up to you whether to create a separate home or not. Then you have to specify the mount points. Make sure that the Windows partition is mounted as /media/sda1 and do not format it.
Look at the pictures of this guide [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
> Is there an option of what to Install Ubuntu too?
This question I don't understand.

---

