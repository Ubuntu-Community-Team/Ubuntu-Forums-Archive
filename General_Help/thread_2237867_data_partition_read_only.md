---
title: "data partition read only"
date: 2014-08-04
forum: General Help
---

### Post by frankyboynl on 2014-08-04
hello, I just deleted a partition and named it DATA. when I try to approach it, it seems to be read only and write for 'root'   how can I change the permissions, so that it I can open it and use it to write data to.



thanks in advance, Frank

---

### Post by Bashing-om on 2014-08-04
frankyboynl; Hello;

How are you mounting the partition in question, and what is the file system imposed on that partition ?

Once these 'parameters' are know we can discuss what is required to mount that partition to your specifications.

[INDENT][INDENT]where there is a will
[INDENT][INDENT][INDENT]there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by frankyboynl on 2014-08-04
the file system is ext4 and is mounted on startup, as a partition called DATA

---

### Post by coffeecat on 2014-08-04
> **frankyboynl said:**
> the file system is ext4 and is mounted on startup, 

How? By means of /etc/fstab?

Post the output of this command:

```
mount
```

And the contents of your /etc/fstab and I can give you the simple terminal command which will solve this problem for you.

---

### Post by frankyboynl on 2014-08-04
frank@frank-K70IJ:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=frank)
/dev/sda6 on /media/frank/DATA type ext4 (rw,nosuid,nodev,uhelper=udisks2)
frank@frank-K70IJ:~$ 


concerning etc/fstab:   there only seems to be a directory called etc/fstab.d,   which is empty

---

### Post by coffeecat on 2014-08-04
> **frankyboynl said:**
> concerning etc/fstab:   there only seems to be a directory called etc/fstab.d,   which is empty

Have another look. If you didn't have /etc/fstab, your system wouldn't run. /etc/fstab is a file, and we need to see it because:

> **frankyboynl said:**
> /dev/sda6 on /media/frank/DATA type ext4 (rw,nosuid,nodev,uhelper=udisks2)


If this is your data partition, the mountpoint /media/frank/DATA suggests you are mounting it from the file manager, which means it isn't being mounted on startup. However, it is possible to have a line in /etc/fstab using the mountpoint /media/frank/DATA, but that would not be a good idea. I think we need to clarify this point.

---

### Post by frankyboynl on 2014-08-04
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=f2b46099-6bd4-41e7-96a4-82a0b8702d0b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e925d2f0-9b17-4a97-8c01-5ba19ebc62b3 none            swap    sw              0       0

---

### Post by coffeecat on 2014-08-04
OK - you are not mounting the data partitioner on startup, but from the file manager. There is no line for your data partition in /etc/fstab. If you want help adding a line to /etc/fstab in order to mount the partition on startup, then post the output of this command:

```
sudo blkid
```

And I can help you with that.

In the meantime, the command to adjust the ownership of your data partition is:

```
sudo chown frank:frank /media/frank/DATA
```

Before you run that, make sure the partition is mounted the way you did it before and is mounted on /media/frank/DATA.

---

### Post by frankyboynl on 2014-08-04
frank@frank-K70IJ:~$ sudo blkid
[sudo] password for frank: 
/dev/sda1: UUID="f2b46099-6bd4-41e7-96a4-82a0b8702d0b" TYPE="ext4" 
/dev/sda2: LABEL="Reservado pelo Sistema" UUID="C47C3CBD7C3CABD4" TYPE="ntfs" 
/dev/sda3: UUID="2C8E40BF8E408376" TYPE="ntfs" 
/dev/sda5: UUID="e925d2f0-9b17-4a97-8c01-5ba19ebc62b3" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="b33b57b0-882a-423a-8f40-8a9629389b77" TYPE="ext4" 
frank@frank-K70IJ:~$

---

### Post by coffeecat on 2014-08-04
Have you run the chown command I posted yet? Did that work?

To have your data partition mounted by means of /etc/fstab, I would suggest creating a mountpoint in /media so that the moounted partition shows in the left pane of your file manager, but not using the /media/username/mountpoint convention that udisks creates. It's tidier keeping the two distinct. So this is what I recommend:

1 – Create your mountpoint. In a terminal:

```
sudo mkdir /media/DATA
```

2 – Check to see if you have gksu installed so that you can run gedit with root privileges. You don't say whether you are using Ubuntu or a derivative or which version of Ubuntu. I'll assume Ubuntu with Unity 14.04.

```
sudo apt-get install gksu
```

If it tells you gksu is already installed, then fine. If not, install it.

3 – Open /etc/fstab in gedit with root privileges:

```
gksu gedit /etc/fstab
```

If you are running another desktop or flavour of Ubuntu and you don't have gedit, post back.

4 – Add this line to the end of /etc/fstab:

```
UUID=b33b57b0-882a-423a-8f40-8a9629389b77     /media/DATA     ext4     defaults     0 2
```

Your /etc/fstab should now look like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=f2b46099-6bd4-41e7-96a4-82a0b8702d0b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e925d2f0-9b17-4a97-8c01-5ba19ebc62b3 none            swap    sw              0       0

UUID=b33b57b0-882a-423a-8f40-8a9629389b77     /media/DATA     ext4     defaults     0 2
```

Save.

**If** you have successfully chown'd your data partition with the command I posted, and **if** you can now save files to it, you can remount it from /etc/fstab with these commands:

```
sudo umount /media/frank/DATA
sudo mount -a
```

With the new line in /etc/fstab your data partition will now be mounted automatically each time you boot up.

---

### Post by frankyboynl on 2014-08-04
thank you so much, this indeed worked for me.


grtz, Frank

---

