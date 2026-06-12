---
title: "file permissions question"
date: 2008-06-12
forum: General Help
---

### Post by ducttapemasterJ on 2008-06-12
Ok this seemed like it should be an easy thing to do, but apparently Im missing something:
I have my computer dual booted with Ubuntu and Windows XP.  I also have a drive that is shared between them, with an NTFS file system. For some reason I seem to be completely unable to chown the files and folders in that drive. They appear all to be owned by "root" and running the chown command does nothing. Any ideas?

---

### Post by geirha on 2008-06-12
That is because NTFS does not support permissions. Linux solves this by setting the same permissions for all files and folders of the drive when its mounted. To change those permissions, you need to change the mount-options for that partition in /etc/fstab. 

You might want to add something like uid=yourusername,gid=somegroup to the options field. «man mount» will tell you all the options you can use for ntfs-3g, or you can paste the output of «grep ntfs /etc/fstab» here to get someone to help you out with what options you should use.

---

### Post by demonhunter5110 on 2008-06-12
Im having the same issue not being able to edit my files on ubuntu 8.04. i also have a duel boot system with ubuntu on my slave drive. i recently was trying to edit the daemon.conf file but was stopped from an error telling me i dont have permission) to save what i just edited. when i looked a bit further into the properties of the daemon.conf. it tells me im not the owner . if i need to change my etc/fstab to enable permissions what do i need to change? heres the etc/fstab information:
 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=bfa01355-65b4-4e75-9d92-76e93b892f6a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=78b50d42-3747-49fa-b591-887438407212 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

any help would be great.

---

### Post by iaculallad on 2008-06-12
Usually, editing system configuration files requires you to have a root/sudoer's priveledge in order to modify it and does not require you to change the entire drive permission.

---

### Post by simonasambler on 2008-06-12
You can also install mc ```
sudo apt-get install mc
``` and login in terminal as root by command ```
su
``` than type mc and work with files as root. Other choice is to install Krusader ```
sudo apt-get install krusader
``` which is much more user friendly, start it and use key alt+k to start krusade in root mode /both are file manager like dos commander and total commander/. 
You can also umount you drive and mount with command ```
sudo mount /your/device /whereto/mount -t ntfs -rw
```
And finally when you want to mount you disk at start you have to edit fstab ```
 sudo gedit /etc/fstab
``` but this option was here describe.

---

### Post by demonhunter5110 on 2008-06-12
thanks so much for the feed back on file permissions. been a great help

---

### Post by ducttapemasterJ on 2008-06-13
Thanks so much for the help, that's definitely getting me pointed in the right direction.  does the fact that NTFS doesn't support file permissions going to mean that I can't share a drive on my linux OS that is formatted in NTFS?  Here is my /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=31683ee8-d957-42db-a70c-20e09a16d557 /               ext3    defaults,errors=remount-ro 0 $
# /dev/sda2
UUID=466855A96855990F /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=5E746197746172A7 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=c301eb6c-bc6c-4caf-9f6f-58f31f72b324 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


how can I get it so that my user: "justin" userid: 1000 can have all priviledges on sda5 and also share it on a network?

---

### Post by geirha on 2008-06-13
> **ducttapemasterJ said:**
> 
# /dev/sda2
UUID=466855A96855990F /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=5E746197746172A7 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1


In this case you are using ntfs instead of ntfs-3g. ntfs does not support writing, while ntfs-3g does. I'd try changing them to:
```

# /dev/sda2
UUID=466855A96855990F /media/sda2     ntfs-3g  defaults,fmask=117,dmask=007,uid=1000,gid=46 0       0
# /dev/sda5
UUID=5E746197746172A7 /media/sda5     ntfs-3g  defaults,fmask=113,dmask=002,uid=1000,gid=46 0       0

```

In this case sda2 is readable and writable to user with uid 1000 and members of the group with gid 46, and inaccessible to everyone else. sda5 is readable by everyone, but only writable by uid 1000 and gid 46.

Gutsy and newer should have the ntfs-3g driver readily available, for older releases, you'll need to install it [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by ddales on 2008-06-13
I had the same problem until I stumbled across a posting which clarified the sharing problem mounting RW.

You MUST set the UID and GID, otherwise, Ubuntu will mount the drive with write permissions only for root.

---

