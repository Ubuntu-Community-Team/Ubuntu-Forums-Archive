---
title: "Storage and partition problems"
date: 2008-03-11
forum: General Help
---

### Post by phunbaba on 2008-03-11
I've got a few strange issues. Using a search got me no results, sadly. I hope someone can help, it's pretty frustrating..

First off. I can't rename my hard drive partitions. It doesn't say why, it just says no. I don't like seeing "DRV1_VOL5" <__<...

Secondly. I have a 160gig ext3 HD that hosts the OS, and I couldn't get it to partition into a 30/130 or whatever I choose.. And I also have a 250gig NTFS HD originally formatted with windows xp pro, which only read 170gigs instead of 250.. And now that i'm using ubuntu, the remainder of the gigs have appeared........somehow.....partitioned by themselves?? Not evenly either!!

Thirdly. In order to access any partition or any other (aside from filesystem, which is the 160 gig), I must put in my password and then it creates a shortcut on the desktop which is not removable. When restarting, this all disappears and I have to do it again.

I am thinking it's from being NTFS, but I'm not sure and I was hoping someone with more ubuntu knowledge would know some of this.

If anyone can help, I really appreciate it.

---

### Post by logos34 on 2008-03-11
You should be able to use tune2fs to name the ext3 partition(s):

sudo tune2fs -L newlabel /dev/drive

As for root, you might try booting from the live cd and using gparted to shrink it down and add another partition.  Not sure why it wouldn't let you during install (although '30/130' won't work simply because your actual total disk space is more like ~150GB).  

You might want to backup whatever is on the ntfs drive and just wipe it clean and start fresh.  Delete all partitions on it with gparted and then create new ext3 parittion(s).

The mounting issue is usually fixed by editing /etc/fstab.  
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

---

### Post by phunbaba on 2008-03-11
Thanks very much.

I'll try that when I get home, currently stuck at work. D:

---

### Post by Omnios on 2008-03-11
K gparted in Ubuntu will not be able to modify partitions that are in use but Ubuntu as they have to be unmounted. I downloaded and used the gparted live cd and it worked like a charm. You should be able to see all the hard drive info and resize and repartition the hard drives. 
 
 As for the hard drive names this can be  changed by going into the /filesystem..  /media file and create files with the names you want to have for the partitions. Then go into fstab and change the mount points which are file names, example bla bla 123 and change the mount adderess to the new file names. They are case sensative and must be the same as  the new files. Linux handles the mount points as files. 
 
 If all is good you can then reboot and the partition names will be the new names.
 
 There is a fstab entry in my sig that explains fstab mounting.

---

