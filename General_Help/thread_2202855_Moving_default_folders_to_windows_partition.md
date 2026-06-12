---
title: "Moving default folders to windows partition"
date: 2014-01-31
forum: General Help
---

### Post by wt-pm66 on 2014-01-31
I'm dual-booting Kubuntu 13.10 and Windows 7, I very rarely use Windows but I do have a couple of programs, that just don't work well with Linux. I do need to be able to access a central folder for Documents/Music/Pictures etc.... So based on some research I did when setting up my Linux system, the best idea I came up with was to place those folders on the windows partition, and change the directory listing to reflect the new address. So for about two and a half weeks everything went fine, then about a week ago I went to open the Documents folder, I clicked the shortcut I put on Dolphins side bar, and get an error that the folder address did not exist. So I went back into system settings, and reset all folders to the windows partition address. Next day, the shortcut was gone again. Now it to the point that I set the address in system settings, close that click my shortcut folder, and get the address does not exist error. If I go through the long way, "Devices>Windows>Documents, it goes through fine. I just cant keep the shortcut working. Right-click and save to Documents, folder does not exist. How can I make this stick?

---

### Post by oldfred on 2014-01-31
If doing this you both need a separate NTFS shared partition and mount NTFS partition with fstab so it is always there for links to work.
Writing directly into the Windows system partition can eventually lead to issues. Most often caused by hibernation, which you should never use anyway when dual booting.

If using NTFS, you cannot explicitly set ownership & permission, but only have defaults that you set with fstab.
       HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)


 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

Older but still useful.

 Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data older but still relavent
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

