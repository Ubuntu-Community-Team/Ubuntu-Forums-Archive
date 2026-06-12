---
title: "Programs can't see files on non-OS partition"
date: 2015-09-18
forum: General Help
---

### Post by lava2 on 2015-09-18
This should be an easy one. 

I have my HD split into two partitions - one that Ubuntu is installed on, the other as an Ext4 partition for my personal files. In Ubuntu I'm able to (auto)mount the drive and browse it with no problems, even open the files in their respective programs. Most programs have an open file dialogue that includes the drive in the sidebar. However, some of the programs installed in Ubuntu can't see that Ext4 partition, so I can't utilize the files there in the programs in question. How do I fix that?

It's happened to me on a few different occasions, and tonight it's happening in Tracktion (for Linux). 

Thanks!

---

### Post by decrepit on 2015-09-18
Are you saying you can't browse to the mount point, where ever that is?

---

### Post by sotiris2 on 2015-09-18
I think its a simple confusion over how the linux filesystem works. In windows you go to my computer and all filesystems are there separately, represented as a letter (i.e. C). So your windows install is on C:\Windows while your music  you store on a different drive/partition might be on F:\Music.

Linux does not really do that although for convenience the file manager will show you icons of each discreet filesystem and so will the unity-launcher. These however are simply features of these programs (nautilus and unity) and not of the actual OS which is why some other programs do not show them. They are not bugged or have any problem. 

In linux there is only one unified filesystem starting at **/** . Every other filesystem (another partition, a removamble media like dvd or usb stick) is mounted to a directory (folder) existing in this filesystem. Where mounted means that the contends of that partition appear to be simply the contents of the directory. 

In practice when you browse your other partition the file manager mounts it at /media/username/partition-label and browses to that directory even though it will not show you the actual path. To find the files with a program that doesn't show you the filesystems as file-manager does you have to manually browse all the way up in the filesystem (usually alt+up_arrow if no ui button is provided) and then enter the media folder. 

Be also aware that ubuntu does not automatically mount all your filesystems at startup but only those specified in a configuration file /etc/fstab.  And while file-manager will automount the partitions when you want to use them (as in browsing) other programs will not. 

For example say you want to get Rhythmbox (a music player) to keep track of your music library in your second hd partition you mount the partition via file manager, navigate to your partition with your music and select it. Rhythmbox sees the files and imports them and all is great. Then you reboot, open up Rhythmbox and it can't play your songs saying the files don't exist. This is because Rhythmbox will not mount the partition and it will try to acess an empty or non existing directory. This is because it has no 'knowledge' it was an different device in the first place. If you browse to the partition with file-manager it will be mounted and Rhythmbox will work again. Ofcourse that is neither the recommended nor an elegant solution.

A better solution is to tell the system to mount the partition at a specific folder at startup. You can either do it via direct editing of [fstab]("https://help.ubuntu.com/community/Fstab") or by using the Disks utility (select your partition click on the little gears icon and then edit mount options). In both cases the directory you will mount to must already exist (and preferably be empty although it will not delete the contents just make them inaccessible).

More on the linux filesystem [here]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview")

---

### Post by lava2 on 2015-09-21
That was it, I just didn't know to look for it in /media...

Thanks!

---

