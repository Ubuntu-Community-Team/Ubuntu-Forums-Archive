---
title: "Permission in NTFS mount point."
date: 2006-11-19
forum: General Help
---

### Post by realtiger on 2006-11-19
Hi all

I have followed the ubuntu unofficial guide to mount NTFS partition.
Now I can read and write NTFS partitions.
But I only want to allow root to write to the NTFS partitions. How can I do that?
Thank you.

Here is my fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=82c7944b-bf39-4f8a-a183-8cd4731141a3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=26E40D0EE40CE1C3 /media/sda1     ntfs-3g     defaults,locale=en_US.utf8,umask=007,gid=46   0    0
# /dev/sda5
UUID=47E7B983A057B4A4 /media/sda5     ntfs-3g     defaults,locale=en_US.utf8,umask=007,gid=46   0    0
# /dev/sda3
UUID=9247f1a5-ce9d-48be-bcb4-2a0264785543 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

Here is the Permission of a NTFS partition mount point, what is plugdev group, I can't find it in Users and Groups Utility.
[IMG]http://freewebtown.com/opensky/upload/p.png[/IMG]

---

### Post by hal10000 on 2006-11-19
I guess it's ok if you delete the enty umask=007,gid=46 in each of the lines.
But take care that you don't change anything else in the lines of your /etc/fstab.
you can edit the /etc/fstab file by using [COLOR="Red"]sudo gedit /etc/fstab[/COLOR] (or instead of gedit any other editor you like)
It may be a good idea to first backup your fstab: [COLOR="Red"]sudo cp -a /etc/fstab /etc/fstab.bkup[/COLOR] before you edit it.
The new lines should look like:
```
UUID=26E40D0EE40CE1C3 /media/sda1     ntfs-3g     defaults,locale=en_US.utf8   0    0
UUID=47E7B983A057B4A4 /media/sda5     ntfs-3g     defaults,locale=en_US.utf8   0    0
```
If you delete the umask and gid entries then the default is used, which is to use the permissios of the user who started the process; if you mount it at boot-time, then it is root who started it.

After you saved the fstab you can test your new configuration:

As a normal user type: [COLOR="Red"]umount /media/sda1[/COLOR] and if it complaints about "you don't have permission to unmount ....." then we are on the right way. Now try [COLOR="Red"]sudo umount /media/sda1[/COLOR] and [COLOR="Red"]sudo umount /media/sda5[/COLOR]. If you get no complaint you have now unmounted both of your windows-partitions.
Now try again to mount them as normal user: [COLOR="Red"]mount /media/sda5[/COLOR] (resp. /media/sda1). It should not work, because you don't have the permission. Again, try it as root ([COLOR="Red"]sudo mount .... [/COLOR]) If it works, then you got it. Try to create a file in your windows-partition as a normal user: [COLOR="Red"]touch /media/sda5/testfile.txt[/COLOR]. It should not work. If you do this with the sudo-command, then you should get a new file called testfile.txt in your windows-partition (sda5).
After the next reboot the new setting take effect.
Hope it helps you.

---

