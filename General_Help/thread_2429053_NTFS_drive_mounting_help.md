---
title: "NTFS drive mounting help"
date: 2019-10-12
forum: General Help
---

### Post by paddy040788 on 2019-10-12
I'm having severe issues auto mounting my ntfs partition as rw.

At this stage I don't know how many different iterations from x amount of different sites in order to try and solve this.

I'm relatively new to linux in general and I believe that i have a generally simple issue, but the amount of bother I am having with this, makes me think I should go back to windows....

My fstab for this drive currently looks like:

/dev/sda1 /media/paddy/TOURO ntfs-3g nls-utf8,umask-0755,uid-1000,gid-1000,rw 0 0
#/dev/sda1 /media/paddy/TOURO ntfs defaults,nls=utf8,umask=000,dmask=027,fmask=137,uid=1000,gid=1000,windows_names 0 0

I have went through various iterations including using UUID, auto type, different dmask, fmasks,uid, gid, copying the options from a known ntfs drive that works as it should being:

/dev/sdd2 /media/paddy/3TB\040HDD auto gid=1000,uid=1000,nosuid,nodev,nofail,x-gvfs-show 0 0

but this did not work as intended for the sda1 drive.

If anyone could help, the amount it would be appreciated would be unbelievable...

---

### Post by oldfred on 2019-10-12
Is Windows hibernated or need chkdsk.
If so then the Linux NTFS driver will not mount NTFS as rw, but only read only. 

Best not to use device like /dev/sdd2, but use UUID or label. Device order can change and then you are trying to mount  incorrect partition. Whenever I plug in a flash drive my device order changes on reboot.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:


I also have seen this as parameters:
nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000

---

### Post by paddy040788 on 2019-10-13
Hi oldfred,

chkdsk worked an absolute treat...

I still had my old hdd with windows(hadn't completely commited to the switch yet) and once I booted up, it ran chkdsk and it appeared to delete a load of thumbs.db files due to invalid filenames and also deleted index entry ECU Emulator.eml:OECustomProperty.

Once completed, I switched back to Ubuntu, used the manual GUI to mount the drive, and could read/write again.

I'll update my fstab following your instructions above.

Thank you so much for helping me out, you have no idea how much this was driving me crazy...:D

---

