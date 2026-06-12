---
title: "Permissions Issue with auto-Mounted NTFS Partition"
date: 2014-01-14
forum: General Help
---

### Post by mblack3nd on 2014-01-14
Hello all and thanks in advance for any help!

I have a partition on this computer set aside for all my files and recently I found I noticed I was unable to save files to the partition. I haven't changed anything with regards to it in some time now and this started a couple of days ago. It seems like a permission issue but I have tried various ways to change the permissions to include me. 

Not sure what to do at this point.

Thanks

---

### Post by Mark Phelps on 2014-01-14
This often happens if you have recently accessed that same partition from inside MS Windows and didn't shut down cleanly when exiting.  Linux then presumes the filesystem is corrupted and won't mount it other than read-only.  Your bet bet is to boot back into MS Windows and do a filesystem check on that partition.

---

### Post by mblack3nd on 2014-01-14
I don't have Windows installed on this computer :(

---

### Post by oldfred on 2014-01-15
If you do not have Windows you maybe should not have an NTFS partition. It wiil need chkdsk periodically like Ubuntu runs fsck every 40 or 60 reboots. If you have a Windows repairCd to run the chkdsk it may be ok.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

   For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

   ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

More info

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
      
 HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by mblack3nd on 2014-01-15
I am going to mark this as solved as I was able to fix whatever the issue was through the app "NTFS Configuration Tools" but it might be worthwhile to figure what caused it...

---

### Post by oldfred on 2014-01-15
Often any of the gui tools do not set up to date parameters for NTFS partitioins. Best to review fstab to see what it did, it also may have used device for mounting like /dev/sda1 which is very old as everything now is UUID as device may change. 
On my system inserting flash drive changes drive order so device even for fixed drives does not work.

---

