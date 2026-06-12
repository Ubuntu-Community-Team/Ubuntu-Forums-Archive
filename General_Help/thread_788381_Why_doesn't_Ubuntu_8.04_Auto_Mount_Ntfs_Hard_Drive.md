---
title: "Why doesn't Ubuntu 8.04 Auto Mount Ntfs Hard Drives anymore?"
date: 2008-05-09
forum: General Help
---

### Post by phildaman46 on 2008-05-09
And why do I get this message when trying to mount one of my Ntfs Partitions?

"Cannot mount volume"
"You are not privileged to mount the volume 'Games'."

---

### Post by macaholic on 2008-05-09
Try loggign in as root then mounting it, not the best soulution by any means, but that's the only way you can do it without editing your /etc/fstab.

---

### Post by wabbster on 2008-05-09
Try this: [http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

As for *why, *well, I don't know. :( (newbie here, sorry!)

Good luck,
Wabb.

---

### Post by phildaman46 on 2008-05-09
How do you login as Root?

---

### Post by didooofidooo on 2008-05-09
first open a terminal and write
sudo passwd root
then give it your password then the new root password
then open System> administration> login window> security
then check beside "allow local system administrator login"
then press alt+ctrl+backspace and login as root

---

### Post by strabes on 2008-05-09
> **didooofidooo said:**
> first open a terminal and write
sudo passwd root
then give it your password then the new root password
then open System> administration> login window> security
then check beside "allow local system administrator login"
then press alt+ctrl+backspace and login as root

I would STRONGLY recommend AGAINST doing this. Logging in as root is extremely dangerous. 

All you have to do is edit your /etc/fstab file.

To edit the file, run this command:```
gksudo gedit /etc/fstab
```

To find the UUID of your NTFS partition, run this command:```
sudo blkid
```

Add a line similar to this: > UUID=XXXXXXXXXXXXXXXXXXXXX /media/windows  ntfs    defaults,umask=007,gid=46 0       1

Replace the XXXXXXXXXXXXXXXXXXXX with with the UUID you found using the sudo blkid command. It will be easiest to just open up two separate terminals for this.

Save the file and run ```
sudo mount -a
```

---

### Post by phildaman46 on 2008-05-09
Logging in as root didn't work. Why am I having a problem with this? It worked before.

---

### Post by wabbster on 2008-05-10
When I had a problem like the one you mentioned, all I did was install NTFS-Config from Synaptic and run that when no drives are mounted. Worked like a charm.

Good Luck,
Wabb.

PS: There are, of course, other methods to do this, but me being a non-terminal user, found this to be easiest. :)

---

### Post by phildaman46 on 2008-05-10
I have NTFS-Config installed already, but still no luck.

---

### Post by wabbster on 2008-05-10
Hm... Did you check all the checkboxes when the dialog box? You'll find the program under Applications>>System Tools.

Here's a screenshot...

Good luck,
Wabb.

---

### Post by phildaman46 on 2008-06-11
Directly from my "Ubuntu Stops Mounting My NTFS Partitions" post where I get no answers:

Randomly, when I restart my computer the mtab file changes and removes my NTFS partitions. Which are "/dev/sdb1 /media/Boot fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sdb5 /media/Games fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0"

This is really annoying. How do I fix this? I even tried to make the mtab file read only, but it still gets modified and erases my NTFS entries.

This is how my mtab is and should be when it works unchanged:
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-18-generic/volatile tmpfs rw 0 0
/dev/sda3 /home ext3 rw,relatime 0 0
/dev/sdb1 /media/Boot fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sdb5 /media/Games fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/user/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=(username) 0 0

---

### Post by paulfeakins on 2009-03-20
I too had this problem after I updated Ubuntu until I installed ntfs-config.

Strangely it didn't show up in the package manager when I typed "ntfs" I had to type "ntfs-config" before it showed up. 

Once installed and the drive was configured, I was able to access it again in the normal way.

---

