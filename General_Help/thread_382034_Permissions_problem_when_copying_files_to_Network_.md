---
title: "Permissions problem when copying files to Network Drive (samba)"
date: 2007-03-11
forum: General Help
---

### Post by gavinjb on 2007-03-11
Hi,

I have a Network hardrive which I connect to through samba and I have setup mount points in fstab, but whenever I try to copy files I get an error message reporting that it could not change permissions for file and a simular message when copying files in the console.

I know this is due to the user and not an error with the Network drive, as when I try to copy files with root (sudo) then I have no problems.  This is causing me a major problem now as I am trying to setup an backup to the drive using rsync, but when copying the files I get the following error

```

rsync: failed to set times on "/media/Backup/.": Operation not permitted (1)
rsync: failed to set times on "/media/Backup/FSM": Operation not permitted (1)
rsync: mkstemp "/media/Backup/.About_Bibble_4.9.0.pdf.Z818EK" failed: Operation not permitted (1)

```

I have tried dismounting the drive and chmod 777 to the mount point (/media/Backup) but this had made no difference

Thanks,


Gavin,

---

### Post by Pontiac on 2007-03-12
Try changing to your /media directory then run the following as root.

chmod -R 0777

I've got a single Ubuntu box serving files.  I've just checked on my box and I see that the folder is set as root:root being the owner.

I would also check the smb.conf file and make sure that you've not set it so that its read-only.

---

### Post by gavinjb on 2007-03-12
Thanks found the easiest way was to use cifs instead of smb (much faster transfer rate as well), as per the details in the following thread

[http://ubuntuforums.org/showthread.php?t=375563&highlight=mount+samba](http://ubuntuforums.org/showthread.php?t=375563&highlight=mount+samba)

---

