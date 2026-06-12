---
title: "i cant see my partitions"
date: 2008-01-21
forum: General Help
---

### Post by mustafa_cmpe on 2008-01-21
it says when click on my partition   

[B]
message box appears
[/B]


cannot mount volume "

Unable to mount the volume 'mustafa'.

---

### Post by banewman on 2008-01-21
Need some more info mustafa
I guess it is a partition that is mounted at boot and you're clicking an icon
Can you post the contents of /etc/fstab - it is the file that mounts partitions at boot
and can you open a terminal and type - 
fdisk -l
and post that here as well please
:)

---

### Post by mustafa_cmpe on 2008-01-21
ok 

in my computer i have 4  partitions  2 of them for ubuntu because it requires like that the other 2  windows and mustafa. Now i am using live cd because the installed ubuntu cannot see my parttions microsoft windows is not opening at all,  only in live cd  i can see partitions 

 when click on them  the message box appears like that 


Cannot Mount Volume 

Unable to mount the volume 'mustafa'.

then  i clicked details button DETAILS> 

then it says like that  

$logFile  indicates unclean shutdown (0, 1) Failed to mount " /dev/sda ": Operation not supported Mount is denied because NTFS is marked to be in use , Choose one action:

Choice 1: IF you have windows then disconnect the external devices by clicking on the "safely remove hardware " icon in windows taskbar then shutdown windows cleanly. 


I cannot access windows not opening at  all 


Choice 2: if you dont have windows then you can use the "force" option for your own responsibility . For example type on the command line : mount-t ntfs-3g/dev/sda/media/mustafa -o force or add the option to relevant row in the  /etc/fstab file  /dev/sda/media/mustafa ntfs-3g defaults , force 0 0
 

but these are happens on live cd other ubuntu which is on my partiion is working it doesnt show my partition at all thats all my problem i hope problem will be solved

---

### Post by mustafa_cmpe on 2008-01-21
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

---

### Post by banewman on 2008-01-21
Open a terminal in the live cd and type - 
fsck -V /dev/sda
and that should try to repair the system and let you know what it is doing along the way.
:)

---

### Post by mustafa_cmpe on 2008-01-21
ubuntu@ubuntu:~$ fsck -V /dev/sda
fsck 1.40.2 (12-Jul-2007)
[/sbin/fsck.ext2 (1) -- /dev/sda] fsck.ext2 /dev/sda 
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Permission denied while trying to open /dev/sda
You must have r/w access to the filesystem or be root
ubuntu@ubuntu:~$

---

### Post by banewman on 2008-01-21
sudo fsck -V /dev/sda
should work then
:)

---

### Post by mustafa_cmpe on 2008-01-21
not working same messages whem i click on parttion mustafa
:(

---

### Post by mustafa_cmpe on 2008-01-21
sudo fsck -V /dev/sda
fsck 1.40.2 (12-Jul-2007)
[/sbin/fsck.ext2 (1) -- /dev/sda] fsck.ext2 /dev/sda 
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?

---

### Post by banewman on 2008-01-21
You might have to bite the bullet and type -
mount-t ntfs-3g/dev/sda/media/mustafa -o force 
as you posted above.
What caused the bad shutdown?

---

### Post by mustafa_cmpe on 2008-01-21
i think so bad shutdown electicity gone any way what should write exactly ntfs-3g/dev/sda/media/mustafa -o

this give command not found

---

### Post by mustafa_cmpe on 2008-01-21
should i write like this ntfs-3g/dev/sda/media/mustafa -o

---

### Post by banewman on 2008-01-21
I copied that command from your second post - redo the steps that gave you those options then copy and paste them in a terminal and see if it works.
Do you have ntfs-3g installed so you can write to your windows partition?

---

### Post by mustafa_cmpe on 2008-01-21
bash: ntfs-3g/dev/sda/media/mustafa: No such file or directory

---

### Post by mustafa_cmpe on 2008-01-21
i dont know ntfs 3g  installed or not

---

### Post by mustafa_cmpe on 2008-01-21
i have to  go now i will write again to you ok thank for helping.

---

