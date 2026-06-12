---
title: "Ubuntu 14.04 restore causes rename of device ?"
date: 2014-10-18
forum: General Help
---

### Post by johan19 on 2014-10-18
During a software upgrade my machine rebooted unexpectedly - causing the 'no system tray' error.
I thought quickest way would be to restore a backup.
However - after the backup I could not run Virtualbox, and noticed that one of my hard disks are now mounted with a different name ?
It used to be 'Disk 1 TB' - now when I look at the Properties - it is called 'Disk 1 TB1'  a digit '1' has been added.

I now see /media/Disk 1 TB/   but it is empty
I also see /media/johan/Disk 1 TB/
as well as /media/johan/Disk 1 TB1/

However - under Devices in Files - I see Disk 1 TB  only - (the properties however is Disk 1 TB1)

The properties of  /media/johan/Disk 1 TB/  has a location of /media/johan - free space of 10GB (no Volume)
The properties of  /media/johan/Disk 1 TB1/  has a location of /media/johan and also Volume: Disk 1 TB - showing the disk info, free space etc...
I cannot copy from TB1 to TB as there is not enough space..

I thought quick solution would be to rename  /media/johan/Disk 1 TB/  -> whatever and
rename  /media/johan/Disk 1 TB1/ ->  /media/johan/Disk 1 TB/ 

Unfortunately that does not seem possible with the GUI ...?

I am quite prepared to do a restore again - I just want my old machine back....
Not a Unix expert at all - so I am a bit stressed....

Any help would be greatly appreciated?

---

### Post by TheFu on 2014-10-18
I don't have an answer ... 

however .... stuff mounted under /media is generally named based on the disk labels of the partitions. Seems the label got renamed or the old mount point is in-use?  

Also - having spaces in files/directories causes some hassles and some scripts will fail to work correctly. I know that mine won't - because I'm lazy. It is best to avoid using spaces in any directory or filename - also avoid ' and " in these.

---

### Post by johan19 on 2014-10-19
Thanks for your post. 
I found out the mount point was incorrect - somehow the restore caused it to mount to /media/johan/'Disk 1 TB1' - have no idea why....
I managed to fix it by :

1. Unmounting the 1 TB disk, and then mounting it to the mount point it should be mounted to :
2. sudo mount /dev/sda /media/johan/'Disk 1 TB'

Now my VirtualBox is working again.

Question : How do I change it so it ALWAYS mounts to this mount point?

---

### Post by O9aIevckc0 on 2014-10-19
you could add it to your /etc/fstab then it should always mount to the same place

(if this solves your problem please mark this thread as solved)

---

### Post by johan19 on 2014-10-22
Thanks !

---

