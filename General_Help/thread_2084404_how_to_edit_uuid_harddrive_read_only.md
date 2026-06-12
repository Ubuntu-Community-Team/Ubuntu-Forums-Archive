---
title: "how to edit uuid harddrive read only?"
date: 2012-11-15
forum: General Help
---

### Post by jebi on 2012-11-15
hi
 
i have been told what i need to to is make my non ext4 partitions read only or better yet make it so that ubuntu does not have the authority to read them..
 
i did get the basic info on how to do this and i tried but i failed to do it correctly.
 
please please please could someone do a youtube video tutorial?, or a complete idiots noobs guide with screen grabs...
 
fstab or uuid...
 
i need every step spelling out, i am looking to use ubuntu as my default os, but not until i get better at it..
 
many thx
 
ps i am a complete noob to ubuntu, so please dont just say oh just edit with x app and blah
 
thx

---

### Post by cj13579 on 2012-11-15
Is this as part of a dual boot? If so, you could disable auto mount for those drives (remove the entry from fstab) or just unmount them with umount:

List file systems currently mounted:
NOTE: You're UUID's and devices may look different to mine. You will have to adjust the umount command and the UUIDs to your environment.

```
chris@q2server:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              73G   18G   51G  27% /
none                  497M  288K  497M   1% /dev
none                  501M     0  501M   0% /dev/shm
none                  501M  664K  501M   1% /var/run
none                  501M     0  501M   0% /var/lock
none                  501M     0  501M   0% /lib/init/rw
/dev/sdb1             190G  187G  3.8G  99% /media/stuff
/dev/sdd1             466G  299G  168G  65% /media/external-ma
```

Then unmount the drive that you don't want ubuntu to be able to access:

```
chris@q2server:~$ sudo umount /media/external-ma
```

To do it permanently:

Get the UUID of the disk:

```
chris@q2server:~$ sudo blkid
/dev/sda1: UUID="0a2368b1-bf34-4b77-9569-58ce05c7b673" TYPE="ext4" 
/dev/sda5: UUID="49c4a4fa-165a-4aab-907c-218f1294771a" TYPE="swap" 
/dev/sdb1: LABEL="STUFF" UUID="D3E2-26FF" TYPE="vfat" 
/dev/sdd1: LABEL="external-ma" UUID="A4E3-407A" TYPE="vfat" 

```
Backup fstab:

```
chris@q2server:~$ sudo cp -p /etc/fstab /etc/fstab.orig
```

Edit fstab:

Now you have options. If you want to not have the drive available at all simply remove the line for the appropriate UUID. If you want to see the drive but not be able to write to it, simply remove the "w" from the appropriate line. You can see more on fstab [here]("https://help.ubuntu.com/community/Fstab").

```
chris@q2server:~$ sudo nano /etc/fstab
```

Or if you want a GUI editor:

```
chris@q2server:~$ gksudo gedit /etc/fstab
```

The line you want will start with the UUID of the drive(s) that you want to remove/change:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0a2368b1-bf34-4b77-9569-58ce05c7b673 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=49c4a4fa-165a-4aab-907c-218f1294771a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=A4E3-407A /media/external-ma vfat rw 0 0
UUID=D3E2-26FF /media/stuff vfat rw,uid=1000,gid=1000 0 0
#/dev/sdd1  /media/silver  ext3  defaults  0  0
```

You will need to restart your machine for fstab changes to take affect.

Hope that helps

---

### Post by Morbius1 on 2012-11-15
> i have been told what i need to to is make my non ext4 partitions read  only or better yet make it so that ubuntu does not have the authority to  read them..That's 2 different things and I don't know what you mean by non ext4 partitions. Does that mean NTFS and FAT32 or do you include ext3 in that definition?

Let's assume you mean NTFS partitions. [COLOR=Blue]**This is an example of the process**[/COLOR] and I'll do it in a way to make it simpler to change from no access to read only access:

[1] Create a mount point for the partition:
```
sudo mkdir /mnt/NTFS1
```[2] Run the following command to get the UUID number for that partition:
```
sudo blkid -c /dev/null
```[3] Edit fstab as root:
```
gksu gedit /etc/fstab
```[4] Decision time.

** If you want Ubuntu to not mount the partition and disable the graphical way to mount it then add this line to fstab:
```
UUID=200C11850C1156DE /mnt/NTFS1 ntfs defaults,noauto,umask=222 0 0
```** If you want it to mount but with read only access then just remove the noauto option:
```
UUID=200C11850C1156DE /mnt/NTFS1 ntfs defaults,umask=222 0 0
```[COLOR=Blue][I]In either case the correct UUID number for your partition is in the output of the blkid command.

[/I][COLOR=Black][5] Either reboot the box or unmount the ntfs partition if it is currently mounted and run the following command to put the fstab additions in affect:
[/COLOR][/COLOR]```
sudo mount -a
```[COLOR=Blue][COLOR=Black]
[/COLOR][/COLOR]

---

