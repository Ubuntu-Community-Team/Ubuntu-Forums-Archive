---
title: "Problems in Dell Inspiron 3521 after installing 14.04 alongside Windows 8"
date: 2014-10-22
forum: General Help
---

### Post by davy jones on 2014-10-22
I have an NTFS  data partition on my hard disk, and I need it to mount on startup. I  read somewhere this can be done using Disks, so I followed the  instructions and switched off the Automatic Mount Options for that  partition. After I restarted, I saw that this had created a problem  because earlier, this partition was mounting at /media/<username>,  but suddenly there was a mnt folder in / and that became the mount  point of the partition. There were also Bootinfo and boot-sav folders in  this mnt folder, and a boot-sav folder in / as well. I undid what I had  done in Disks, and on restart, the partition was mounting at  /media/<username> again but the mnt, bootinfo, boot-sav folders  were still there. I need to know whether these folders should be  deleted, and if yes, then how. Also, I need to find a way to get my data  partition to mount on startup.

Any  help would be appreciated, and since I'm not very tech-savvy simplified  instructions would be even more appreciated. Thanks in advance.

---

### Post by Bucky Ball on 2014-10-22
Sounds like you had the menu bar hidden in Nautilus. That is an option. I think there's a key combination that hides/unhides. You might be able to research that.

If you have more than one support request please post seperate threads for each, one request a thread. Gets too confusing trying to fix five things on the one thread. Thanks and good luck.

---

### Post by davy jones on 2014-10-22
Edited, thanks.

---

### Post by Bucky Ball on 2014-10-22
Apparently you hit alt+m to hide/unhide the menu bar in Nautilus. Try it.

---

### Post by davy jones on 2014-10-22
I'm actually happy using Nemo, because it has more features. Still nothing on the thumbnail front though.

---

### Post by davy jones on 2014-10-23
Would like help with getting my data partition to mount on startup ASAP as I don't want to risk trial and error given that it hasn't worked out so well for me. Thanks.

---

### Post by davy jones on 2014-10-23
I have an NTFS  data partition on my hard disk, and I need it to  mount on startup. I  read somewhere this can be done using Disks, so I  followed the  instructions and switched off the Automatic Mount Options  for that  partition. After I restarted, I saw that this had created a  problem  because earlier, this partition was mounting at  /media/<username>,  but suddenly there was a mnt folder in / and  that became the mount  point of the partition. There were also Bootinfo  and boot-sav folders in  this mnt folder, and a boot-sav folder in / as  well. I undid what I had  done in Disks, and on restart, the partition  was mounting at  /media/<username> again but the mnt, bootinfo,  boot-sav folders  were still there. I need to know whether these folders  should be  deleted, and if yes, then how. Also, I need to find a way to  get my data  partition to mount on startup. 

I would nornally do some trial and error but that has really not worked so well for me in the recent past. Quick help would be appreciated, and since I'm not very tech-savvy  simplified  instructions would be even more appreciated. Thanks in  advance.

---

### Post by coffeecat on 2014-10-23
First of all, don't delete the /mnt folder. That always was there - you must have missed it before. It's a valid place to mount devices but I prefer not to use it for most occasions, because if you mount a partition in /mnt or a sub-folder of /mnt, you don't get a launcher icon or see it appear in the list in the left pane of Nautilus. If you mount a partition in a sub-folder of /media, you get both, which is much more convenient, imo. Other people differ, and prefer /mnt - variety being the spice of life and all that. 

As far as the bootinfo and boot-sav folders are concerned, if they are empty they are not doing any harm.

I've noticed that Disks can be used to ensure that partitions are automounted on startup, but I've also noticed threads here detailing problems with this and have never used this myself. I must admit, if Disks is creating /mnt/bootinfo and /mnt/boot-sav folders, I'm left scratching my head wondering about the rationale for this. My preference is to edit /etc/fstab manually, even though it is not particularly newbie-friendly.

Since you are talking about a NTFS partition, you might find this wiki page useful:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Before you do anything, let's see if there is a residuum in your /etc/fstab from what Disks what trying to do, and also some other relevant information. Please post the output of these terminal commands:

```
cat /etc/fstab
mount
sudo blkid
```

Please post your output between [noparse]```
 and 
```[/noparse] tags to preserve formatting and to make it readable.

---

### Post by Bucky Ball on 2014-10-23
Install ntfs-3g and ntfs-config;
You should find 'NTFS configuration tool' in your System menu somewhere;
Run it and configure the partition, the tool will re-write your fstab and the partition should mount at boot.

If that doesn't work:

Open Gparted;
Find which sd** (sda1, sdb2, etc.) the data partition is;
Open a terminal and:

```
sudo mkdir /mnt/data
sudo mount /dev/sd** /mnt/data
```

... where 'sd**' is the identity of your data partition.

Is the partition now mounted? If so, we can make it permanent so it mounts at boot.

---

### Post by coffeecat on 2014-10-23
@davy jones, having responded to your latest thread I see now that it is a duplicate of one you posted a day ago. Please do not post duplicates. This leads to exactly the type of situation you see here, where Bucky Ball and I have both given you valid but varying advice, each not knowing of the other's input.

I have merged the two threads.

---

### Post by davy jones on 2014-10-23
This is the output - 

```
bhaskar@Westeros:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=d5ffb8ca-d907-4d9e-a8f2-5a83c958cedb /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=2C2A-F617  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda9 during installation
UUID=ac6616d9-90d8-48cf-ba7a-29b466e556bf /home           ext4    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=96ff2bf7-5776-4d15-b5d8-c48d97652995 none            swap    sw              0       0
UUID=2C2A-F617    /boot/efi    vfat    defaults    0    1
```

```

bhaskar@Westeros:~$ mount
/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda9 on /home type ext4 (rw)
/dev/sda1 on /boot/efi type vfat (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=bhaskar)
gvfsd-fuse on /home/bhaskar/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev)
/dev/sda12 on /media/bhaskar/Data type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
```

```

bhaskar@Westeros:~$ sudo blkid
[sudo] password for bhaskar: 
/dev/sda1: LABEL="ESP" UUID="2C2A-F617" TYPE="vfat" 
/dev/sda2: LABEL="DIAGS" UUID="DA9A-507B" TYPE="vfat" 
/dev/sda4: LABEL="WINRETOOLS" UUID="92C49BA0C49B855F" TYPE="ntfs" 
/dev/sda5: LABEL="OS" UUID="88329F64329F5652" TYPE="ntfs" 
/dev/sda6: LABEL="PBR Image" UUID="EA32E81032E7E015" TYPE="ntfs" 
/dev/sda7: UUID="d5ffb8ca-d907-4d9e-a8f2-5a83c958cedb" TYPE="ext4" 
/dev/sda9: UUID="ac6616d9-90d8-48cf-ba7a-29b466e556bf" TYPE="ext4" 
/dev/sda10: UUID="96ff2bf7-5776-4d15-b5d8-c48d97652995" TYPE="swap" 
/dev/sda12: LABEL="Data" UUID="365315F110F42CE7" TYPE="ntfs"
```

Sorry for posting multiple threads. I thought the title on this wasn't specific enough. Thanks for the quick replies.

---

### Post by coffeecat on 2014-10-23
I've split your three outputs into three code boxes - it makes it easier to read.

This line:

```
/dev/sda12 on /media/bhaskar/Data type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
```

Tells us that your NTFS Data partition is sda12 and that you are currently mounting it from the file manager. Which means that it is not mounted at startup. If you want it mounted at startup, you can either use the GUI config tool that Bucky Ball mentions - ntfs-config, which is new to me (until Bucky Ball posted I assumed ntfs-config was a an obsolete package of command-line utilities now merged into ntfs-3g; the devs appear to be using the same name in order to confuse everyone!) - or you can add a line to /etc/fstab as described in the wiki link I posted.

If you want to edit /etc/fstab, I would suggest this line:

```
UUID=365315F110F42CE7  /media/Data  ntfs-3g  defaults,windows_names,locale=en_US.utf8  0 0
```

But first you need to create /media/Data with:

```
sudo mkdir /media/Data
```

You will also need to change *locale=en_US.utf8* in the new /etc/fstab line to your locale - that's explained in the wiki link.

If you need help with editing /etc/fstab, do post back, but it should be explained in the wiki. You may need to install the package gksu to invoke gksudo - gksu is no longer installed as default in Ubuntu.

---

### Post by davy jones on 2014-10-23
ntfs-config worked! Thanks a lot!

---

### Post by Bucky Ball on 2014-10-23
Exellent news! Please mark the thread as solved if you are happy it is by following the second link in my signature, and don't hesitate to post a new thread for any further issues.

Good luck. ;)

---

