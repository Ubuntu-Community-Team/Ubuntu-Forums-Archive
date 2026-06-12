---
title: "Help with permissions of a hard drive."
date: 2007-05-10
forum: General Help
---

### Post by lawentzel on 2007-05-10
I have a Windows partition and an Ubuntu Linux partition.  The Windows partition shows up on my desktop.  When I view the permissions they are set as Root: Access data and Plugdev: Access data and Other: nothing.  So when I have attempted to run applications on this drive, it stops as it can't write to the drive.  How do I change those permissions.  Thanks.

---

### Post by taurus on 2007-05-10
If it's a ntfs filesystem, then you need to install ntfs-3g before you can write to your Windows.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by strabes on 2007-05-10
```
sudo aptitude install ntfs-3g
```

Then add the following line to the bottom of your /etc/fstab file:
> /dev/sda1	/media/windows	ntfs-3g	defaults	0	0

You need to replace "sda1" with the /dev location of your windows partition. To find this out you can run ```
sudo fdisk -l
```

Look for the partition that is NTFS.

See this page for more information: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by lawentzel on 2007-05-10
Thank you, that worked perfectly.  I appreciate your help.

---

### Post by jimartin8219 on 2008-01-13
Hello all, 
I just formated 3 hard drives on my system and it will not let me create folders.  I'm new to Ubuntu so go easy on me.

Thanks.

---

