---
title: "Problem copying files from Home to Mounted Partition"
date: 2017-02-16
forum: General Help
---

### Post by holytree2 on 2017-02-16
Hello guys. 
The problem I'm currently facing is this, running Ubuntu 16.10, with cinnamon DE. 
I have files filling up my home partition and I'm trying to move files out, but I am neither able to do stuff like creating new folders neither am I able to copy/paste files/folders to the windows NTFS partitions even though they are mounted. I have tried a method which involved Uninstalling Gparted and ntfs-3g and ntfsprogs but to no effect. 
I have also tried using NTFS configuration tool to no  avail. 

Could anyone help me out? Thanks in advance.

---

### Post by oldfred on 2017-02-16
What version of Windows.

If Windows 8 or 10 have you turned off fast start up. That leaves all NTFS partitions mounted/hibernated. The Linux NTFS driver will not mount NTFS that is hibernated (or needs chkdsk) to prevent damage.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by SeijiSensei on 2017-02-16
NTFS is not a good option for copying entire folders from the ext[234] filesystems that Linux natively uses.  It doesn't support important features like permissions or symlinks.  I've occasionally used tar to create an archive then coping that to an NTFS filesystem for backup purposes.

Ordinary files are less of an issue than folders (directories).

---

