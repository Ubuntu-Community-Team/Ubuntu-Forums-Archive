---
title: "Ubuntu corrupted my lifetime PHOTOS folder..."
date: 2023-10-14
forum: General Help
---

### Post by sametkoy on 2023-10-14
Greetings guys,


Pre-info: 
- Computer: Asus UX32LN laptop 64 bit
- HDD&OS  : Ubuntu 22.04.3 LTS  on 256 GB SSd
- External: WD 1 TB external hard disk where whole my archive is in. NTFS format.


First time I connected my external HDD to Ubuntu laptop. Everything was perfect, It saw my two parted (400GB and 550~GB) HDD without any problem. All the files and folders was visible. Again everything was ok while I only open and close files. Then I decide to organize my photo archive. I had just cut some 10-30 photos from a sub-folder and paste them into main folder. After this operation my whole folder is gone. All I can see is main folder and some 20 pics in it. More than hundred GB folder is completely gone. 


- I am sure I didn't do anything wrong accidentally. 
- HDD is healthy.
- I opened the laptop with a bootable Win10 USB and it sees the folder but folder is empty. Ubuntu can see some 20 files but Win10 can't see that too.
- All other folders on HDD is good, readable by both Win10 and Ubuntu.


When I check the HDD size from gparted, %85 is full. It means It didn't deleted my archive. But where is it? This is my whole life archive of last 15 years and I want to try every possible non-risky way to recover them. 

Thanks.

---

### Post by oldfred on 2023-10-14
Never make major changes without good backups.
If some data is valuable you have good backups, usually in more than one place and version.

With Linux the NTFS driver will not normally open hibernated NTFS partitions. But Windows defaults to Fast Startup which sets hibernation flag. Then any changes from Linux in a NTFS partition are lost when Windows restores the hibernation.

Does teskdisk deeper serch find files. If so immediately copy to another drive.
If not then you have to use Photorec or other recovery tools. Some say Windows tools which may be paid applications work better.
But either way it will take hours to scan a larger drive & copy files. Photorec does not find full filename, just extension. But if Photo you can use uses to rename using internal data in photo.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) & 
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[https://askubuntu.com/questions/3883/how-to-recover-deleted-files](https://askubuntu.com/questions/3883/how-to-recover-deleted-files)

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) 
[https://apps.microsoft.com/detail/9N26S50LN705?hl=en-us&gl=US](https://apps.microsoft.com/detail/9N26S50LN705?hl=en-us&gl=US)
Old info, not sure what if still valid
[https://ubuntuforums.org/showthread.php?t=2247461](https://ubuntuforums.org/showthread.php?t=2247461)

---

### Post by yancek on 2023-10-15
It would be a lot safer to copy/paste than cut/paste when you do NOT have any backups!
You seem to be saying that when you copied/pasted the small number of files, the rest of the contents of the folder immediately disappeared?  Seems unlikely.  More details on exact steps might help someone to help you.  Testdisk and photorec should help but it will be difficult as they don't retain file names.

---

### Post by Impavidus on 2023-10-15
Somehow, the filesystem was damaged. Windows hibernation was already mentioned, but you must also unmount the filesystem before unplugging. Some people just pull it out, which is bad, even on Windows (but Windows has (had?) some safeguards to make it less likely this will result in problems).

Just to be sure, you can clone the drive first. If any file recovery methods make things worse, you'll have a backup of your damaged filesystem.

As your photos are stored on a Windows filesystem, I suggest using Windows tools for recovery.

---

