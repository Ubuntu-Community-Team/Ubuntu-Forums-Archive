---
title: "Windows NTFS partitions"
date: 2005-10-16
forum: General Help
---

### Post by installer on 2005-10-16
Breezy mounts all my NTFS partitions automatically, but the only way to access them is to log in as 'Root' how can I get around this. 

Under 'Hoary' it was easy You just used this procedure......


e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
Append the following line at the end of file 

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
Save the edited file.

-------------------------------------------------------------------------------------------------


But if you do this in 'Breezy' you get nowhere because it's allready mounted any ideas?

---

### Post by ecobuntu on 2005-10-16
what if you do this

sudo chown <yourname> /media/windows

---

### Post by seldenthuis on 2005-10-16
In Breezy the procedure is the same. After modifying /etc/fstab you just have to remount the partition:
sudo mount -o remount /media/windows

---

### Post by installer on 2005-10-16
[QUOTE=ecobuntu]what if you do this

sudo chown <yourname> /media/windows[/QUOTE]

Well I have tried this but as it is already mounted as hda1 I get nowhere, also have tried sudo chown myname /media/hda1 but get this error.....


chown: changing ownership of `/media/hda1': Read-only file system

---

### Post by ecobuntu on 2005-10-16
is /media/windows linked to /media/hda1?

---

### Post by ember on 2005-10-16
I fear, the latter idea won't help, because the permission of the folder where the drive is mounted is ignored. Look at your fstab and edit the corresponding line (there should already be one, inserted by the installer):

# windows partition
/dev/hda1       /media/Windows  ntfs    ro,nosuid,nodev,uid=ember,gid=ember,dmask=0223,fmask=0233,iocharset=utf8

This is what I use, it mount's the partition to my normal username and with permissions r-xr-xr-- for directories and r-xr--r-- for files. That allows me to copy data from my windows partition and to do a simple 'chmod -R u+w folder' and have the standard linux access rights set.

HTH,
ember

---

### Post by installer on 2005-10-16
[QUOTE=seldenthuis]In Breezy the procedure is the same. After modifying /etc/fstab you just have to remount the partition:
sudo mount -o remount /media/windows[/QUOTE]

So would I delete all references to NTFS partitions (that were automatically detected) and then use the 'Hoary procedure?

Here is my fstab (with what I think needs deleting commented with   '?'



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb5       /               ext3    defaults,errors=remount-ro 0       1

?/dev/hda1       /media/hda1     ntfs    defaults        0       0

?/dev/hda5       /media/hda5     ntfs    defaults        0       0

/dev/hdb2       /media/hdb2     ext3    defaults        0       2

?/dev/hdb6       /media/hdb6     ntfs    defaults        0       0

?/dev/hde5       /media/hde5     ntfs    defaults        0       0

?/dev/hdf5       /media/hdf5     ntfs    defaults        0       0

?/dev/hdg1       /media/hdg1     ntfs    defaults        0       0

?/dev/hdg5       /media/hdg5     ntfs    defaults        0       0

?/dev/hdh1       /media/hdh1     ntfs    defaults        0       0

?/dev/hdh2       /media/hdh2     ntfs    defaults        0       0

/dev/hdh3       none            swap    sw              0       0

/dev/hdh5       none            swap    sw              0       0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by seldenthuis on 2005-10-16
I wouldn't delete them if I were you. Just change defaults to umask=0222 for all ntfs partitions and remount them.

---

### Post by installer on 2005-10-18
[QUOTE=seldenthuis]I wouldn't delete them if I were you. Just change defaults to umask=0222 for all ntfs partitions and remount them.[/QUOTE]

Thanks unmask=0222 worked.

---

