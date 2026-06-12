---
title: "Changing media hard disk permissions"
date: 2007-07-02
forum: General Help
---

### Post by Dak1n on 2007-07-02
Hi,

I have a hard disk that I have all my media stored on in ntfs format as this disk used to be in a windows machine but I cannot add any files to it as the permissions for the whole disk are set to root. I have tried in terminal:

sudo chmod a+rwx /media/Files

(Files is the name of the hard disk)

Then it says:

chmod: changing permissions of '/media/Files' : Read - only file system

I installed ntfs-3g and tried:

sudo chown -hR administrator /media/Files

and after it has done all the processes it says

chown: changing ownership of '/media/Files': Read-only file system

and i still cannot edit the files

I'm quite new to Linux so any help would be greatly appreciated.

Thanks.

---

### Post by bmorency on 2007-07-02
can you post your /etc/fstab file?

have you rebooted since you installed ntfs-3g? the partitions might need to be remounted using ntfs-3g.

what does the folder listing look like when you type "ls -l /media/Files" ?

---

### Post by Dak1n on 2007-07-02
hi,

i have restarted since i installed ntfs-3g and re-tried the operations.

when i type 'Is -I /media/Files' i get

-r-xr-xr-x 1 root root    210 2006-12-26 20:42 boot.ini
-r-xr-xr-x 1 root root     40 2007-02-21 22:33 hiberfil.sys
dr-xr-xr-x 1 root root   4096 2007-06-27 20:54 My Music
dr-xr-xr-x 1 root root  16384 2007-06-27 21:25 My Videos
-r-xr-xr-x 1 root root  47564 2004-08-04 13:00 NTDETECT.COM
-r-xr-xr-x 1 root root 250032 2004-08-04 13:00 ntldr
dr-xr-xr-x 1 root root   4096 2007-06-27 20:55 RECYCLER
dr-xr-xr-x 1 root root   4096 2007-06-27 20:55 System Volume Information
-r-xr-xr-x 1 root root    162 2007-06-26 21:14 ~$trokes.doc

thanks

---

### Post by bmorency on 2007-07-02
> **Dak1n said:**
> hi,

i have restarted since i installed ntfs-3g and re-tried the operations.

when i type 'Is -I /media/Files' i get

-r-xr-xr-x 1 root root    210 2006-12-26 20:42 boot.ini
-r-xr-xr-x 1 root root     40 2007-02-21 22:33 hiberfil.sys
dr-xr-xr-x 1 root root   4096 2007-06-27 20:54 My Music
dr-xr-xr-x 1 root root  16384 2007-06-27 21:25 My Videos
-r-xr-xr-x 1 root root  47564 2004-08-04 13:00 NTDETECT.COM
-r-xr-xr-x 1 root root 250032 2004-08-04 13:00 ntldr
dr-xr-xr-x 1 root root   4096 2007-06-27 20:55 RECYCLER
dr-xr-xr-x 1 root root   4096 2007-06-27 20:55 System Volume Information
-r-xr-xr-x 1 root root    162 2007-06-26 21:14 ~$trokes.doc

thanks

can you post your /etc/fstab?  i just want to see if ntfs-3g has made any changes to it.

---

### Post by r0ck80y on 2007-07-02
If you are on feisty, go to System tools --> NTFS Configuration Tool. This will enable the ntfs-3g modules to give write permissions. Or in terminal type "sudo ntfs-config"

---

### Post by mohansoundar on 2007-07-05
I have the same problem :(

I have installed ntfs-3g already and rebooted the machine.

Now I do not have NTFS Configuration Tool in System tools or the command 'ntfs-config' is not available.
I thought ntfs-3g is not installed properly and re-installed it ( It says that its already the newest version )

Am I missing anything ?

---

### Post by Nythain on 2007-07-05
so seriously, gonna have to see your /etc/fstab to see if the appropriate changes were made... just installing ntfs-3g doesnt usually make the needed changes to have the drive mount at boot with the ntfs-3g driver, so rebooting till your mouse buttons fall off isnt going to much untill we see whats goin on with your fstab

---

### Post by Dak1n on 2007-07-05
hi, here it its

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sde1
UUID=d684eecc-2d0a-41cc-8a34-9ccdd765687f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sde5
UUID=284c58e9-c64e-428a-98aa-6ce67b2b85b8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

