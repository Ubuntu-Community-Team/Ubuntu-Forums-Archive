---
title: "external drive file system changed to ntfs. How do I change back?"
date: 2008-04-04
forum: General Help
---

### Post by bigbudz on 2008-04-04
My external drive's file system has been changed to ntfs. It happened after I was downloading files with bittorrent and then when finished I was unable to unmount the drive. I tried to unmount in terminal and that didn't work so I just restarted and everything worked ok. My vista laptop thinks my external drive is corrupt because of the change in file system. It was working fine with both OS before. Does anyone know how to change it back so it can work with both OS again?

---

### Post by tamoneya on 2008-04-04
you can mount ntfs drives in linux now.  But if you want to change it the only way is to reformat the partition by using something like fdisk(CLI) or gparted(GUI).  Note: when you reformat the partition you will lose all the data on it.

---

### Post by bigbudz on 2008-04-04
Thats horrible. Why would Ubuntu do this to my drive?

---

### Post by skydiver|goose on 2008-04-04
that's what formatting does. it takes everything off the drive.

just back up your files to your computer, reformat it for FAT32, then re load your files on there

---

### Post by Raccoon1400 on 2008-04-04
What file system was it before?

NTFS should work in both OSs. If not, maybe the file system is corrupt.

---

### Post by bigbudz on 2008-04-04
I checked the ntfs-3g site and another guy had an issue with Vista thinking a drive with the ntfs file system is corrupt and he thinks it is a Vista bug because XP will recognize his drive. I was using my external drive for months with Vista flawlessly under a Windows file system... (i guess thats what its called). I have no idea how Linux changed the file system and why, but I knew it to check ntfs-3g because after the drive wouldn't unmount I ran ps -e in terminal and saw 'mount.ntfs-3g'.

---

### Post by RelativelyQuantum on 2008-04-04
Sounds like the same bug; but can't you copy the info on the external onto your internal HDD and *then* reformat?

---

### Post by bigbudz on 2008-04-05
Sounds like the same bug; but can't you copy the info on the external onto your internal HDD and then reformat?

I wish I could, but the drive is pretty full. I'm actually finding the ntfs-3g file system to be much more stable with Ubuntu, before I had issues with the drive sponatenously unmounting. 

I'm thinking about sticking with the ntfs and just using the external drive for Ubuntu and wait till Vista fixes their bug. Im sure I can find a pen drive or an old DVD burner to move files between computers for now. 

Is it a good idea to be using ntfs? Has anyone else used it? What is the default file system for Ubuntu? If anyone would like to tell me more about different file systems or perhaps point me to a good site it'd be appreciated.

---

