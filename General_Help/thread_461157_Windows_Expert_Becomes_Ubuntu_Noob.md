---
title: "Windows Expert Becomes Ubuntu Noob"
date: 2007-06-01
forum: General Help
---

### Post by leo7068 on 2007-06-01
I installed Ubuntu last night and have the following issues already:

[B]I can't see data DVDs or my DVD drive.

I can't start Torrents in Azureus after I download.[/B]

More detailed: I wanted to install World Of Warcraft quickly without waiting for updates and installs, so I copied the installed version from my Windows XP onto a DVD to later copy back to Ubuntu after reformat. When I place the data DVD in the drive it told me Unable to mount, so I installed 2 things from Synaptic that looked like NTFS read/write addons. These didn't work.

[B]I followed the steps on this website: [http://doc.gwos.org/index.php/Mount_NTFS_Write_Support#Install_the_Dependencies]("http://doc.gwos.org/index.php/Mount_NTFS_Write_Support#Install_the_Dependencies")
[/B]
However, at the last commands I used some "common sense" coding for my dvd drive. Below is what I did.

[B]gksudo gedit /etc/fstab :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=6f55f8df-69c6-499a-8227-89f447d19769 /               ext2    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0135fc18-d7ed-4055-9649-9f9a6e19cf9c none            swap    sw              0       0
/dev/hdc    /media/hdc ntfs-fuse auto,gid=1001,umask=0002    0    0[/B]

I verified that I was in the NTFS group, but now I don't even see my DVD drive! Please help. I thought Ubuntu would be able to use Data DVDs made in Windows XP. 

After that I installed Azureus and downloaded some torrents, but when I go to open them I get the following errors :
[B]Azureus Error: Failed to access torrent file Ensure sufficient temporary file space available.

Open Error: 'file:///home/leo/Desktop/%5BisoHunt%5DNot a File0The.Number.23.DVD.%5B2007%5D.NTSC.dvdr.torrent ' could not be opened:
Not a File[/B]

Do I need to give Azureus administrator status? How do I do that? Please help me with what should be a simple process.

---

### Post by gdoermann on 2007-06-01
Mounting NTFS drives with write support is easier than what you followed on that page... There is a program called ntfs-3g that will do everything for you.  
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

---

### Post by gdoermann on 2007-06-01
> **leo7068 said:**
> I installed Ubuntu last night and have the following issues already:

[B]I can't see data DVDs or my DVD drive.

I can't start Torrents in Azureus after I download.[/B]

More detailed: I wanted to install World Of Warcraft quickly without waiting for updates and installs, so I copied the installed version from my Windows XP onto a DVD to later copy back to Ubuntu after reformat. When I place the data DVD in the drive it told me Unable to mount, so I installed 2 things from Synaptic that looked like NTFS read/write addons. These didn't work.

[B]I followed the steps on this website: [http://doc.gwos.org/index.php/Mount_NTFS_Write_Support#Install_the_Dependencies]("http://doc.gwos.org/index.php/Mount_NTFS_Write_Support#Install_the_Dependencies")
[/B]
However, at the last commands I used some "common sense" coding for my dvd drive. Below is what I did.

[B]gksudo gedit /etc/fstab :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=6f55f8df-69c6-499a-8227-89f447d19769 /               ext2    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0135fc18-d7ed-4055-9649-9f9a6e19cf9c none            swap    sw              0       0
/dev/hdc    /media/hdc ntfs-fuse auto,gid=1001,umask=0002    0    0[/B]

I verified that I was in the NTFS group, but now I don't even see my DVD drive! Please help. I thought Ubuntu would be able to use Data DVDs made in Windows XP. 

After that I installed Azureus and downloaded some torrents, but when I go to open them I get the following errors :
[B]Azureus Error: Failed to access torrent file Ensure sufficient temporary file space available.

Open Error: 'file:///home/leo/Desktop/%5BisoHunt%5DNot a File0The.Number.23.DVD.%5B2007%5D.NTSC.dvdr.torrent ' could not be opened:
Not a File[/B]

Do I need to give Azureus administrator status? How do I do that? Please help me with what should be a simple process.

Could you see your DVD drive before you followed that wiki?

---

### Post by leo7068 on 2007-06-01
Yes before following that Wiki I saw the drive. I did use synaptic to install NTFS-3G, but afterwards when I clicked on the drive I recieved the same "unable to mount" error.

---

### Post by xir_ on 2007-06-01
i think im having the same error. so any help would be doubly appreciated

---

### Post by voxel on 2007-06-01
data DVDs do not use the NTFS file system, so I'm not sure why you were trying to enable NTFS support?

---

### Post by leo7068 on 2007-06-01
That helps a little.

The real question is why won't my data DVD read or mount?

---

### Post by merlinus on 2007-06-01
Seems you are missing some lines in /etc/fstab.  Here are mine as an example:

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0

-merlin

---

