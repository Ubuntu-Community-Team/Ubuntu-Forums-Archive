---
title: "noob needs help"
date: 2012-11-13
forum: General Help
---

### Post by taffdragon on 2012-11-13
hello this is my first post. i had ubuntu 12.4 on my vista pc and was getting to find it quite good. but i need space so i deleted the partion it was on and now i cant access vista. i get a error message saying

"error: no such partition

grub rescue"

ive reinstalled the same version of ubuntu so i can access my files to burn off and reformat vista but i need to access folders on my desktop that contain photos i cant replace.

basically is there anyway i can access the vista desktop through ubuntu.

thanks in advance.

---

### Post by crushkittykitty on 2012-11-13
When you reinstalled ubuntu was it a side by side install like before or did it just install and delete the whole disk. This is what I would do. boot up a live cd/ usb and then mount the hard drive and see what is there. You might have just erased the whole hard drive when you reinstalled Ubuntu.








[http://ubuntutheotheros.webs.com](http://ubuntutheotheros.webs.com)

---

### Post by dannyboy79 on 2012-11-13
boot up a live cd OR within your ubuntu install show us the output of the following command entered into a terminal session:
```
sudo fdisk -l
```
that will show us yor partition table so we can help you mount your NTFS partition. Do you still want Vista? If so, you could probably use Boot Repair to fix your grub menu so it shows your Vista install so you can boot to it.

---

### Post by taffdragon on 2012-11-13
> **crushkittykitty said:**
> When you reinstalled ubuntu was it a side by side install like before or did it just install and delete the whole disk. This is what I would do. boot up a live cd/ usb and then mount the hard drive and see what is there. You might have just erased the whole hard drive when you reinstalled Ubuntu.








[http://ubuntutheotheros.webs.com](http://ubuntutheotheros.webs.com)


the first time i installed it i created a new partition and installed it there but this time i done a side by side install i think it is, it was the first option on the install disk.

---

### Post by dannyboy79 on 2012-11-13
> **taffdragon said:**
> the first time i installed it i created a new partition and installed it there but this time i done a side by side install i think it is, it was the first option on the install disk.
i can't help until I see your various hard drives and partition tables by using the command I mentioned earlier

---

### Post by taffdragon on 2012-11-13
> **dannyboy79 said:**
> boot up a live cd OR within your ubuntu install show us the output of the following command entered into a terminal session:
```
sudo fdisk -l
```that will show us yor partition table so we can help you mount your NTFS partition. Do you still want Vista? If so, you could probably use Boot Repair to fix your grub menu so it shows your Vista install so you can boot to it.


i can see my windows files and user files through ubuntu just not the ones i need.

i just tried to use the live cd but my dvd drive has stopped working for so reason and it was working a hour ago as i burnt a vista repair disk to try see if that would help.


when i start up the PC i can see the ubuntu and the vista on there but when i click vista it goes so far then goes to the recovery prog but only gives me option for a factory recovery.

is there any way i can start a terminal session without the disk?

---

### Post by dannyboy79 on 2012-11-13
didn't you say you have a working ubuntu install? just open a terminal within that ubuntu install.

now you're saying you can see your files but they aren't the ones you need. not sure what you mean. just post the output from the command i asked to make sure you have all the windows partitions mounted so we can find your files.

---

### Post by taffdragon on 2012-11-13
> **dannyboy79 said:**
> didn't you say you have a working ubuntu install? just open a terminal within that ubuntu install.

now you're saying you can see your files but they aren't the ones you need. not sure what you mean. just post the output from the command i asked to make sure you have all the windows partitions mounted so we can find your files.


right figured out the terminal bit.

heres what it said.

> karl@karl-G31-M7-TE:~$ sudo fdisk -l
[sudo] password for karl: 

Disk /dev/sda: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd848edd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    11949728     5974833    7  HPFS/NTFS/exFAT
/dev/sda2   *    23631615   488391208   232379797    7  HPFS/NTFS/exFAT
/dev/sda3        11950078    23629823     5839873    5  Extended
/dev/sda5        11950080    19439615     3744768   83  Linux
/dev/sda6        19441664    23629823     2094080   82  Linux swap / Solaris

Partition table entries are not in disk order
karl@karl-G31-M7-TE:~$ 

hope thats ok?

---

### Post by dannyboy79 on 2012-11-13
ok, are any of those partitions mounted? you can tell with teh mount command

```
mount
```

---

### Post by taffdragon on 2012-11-13
> **dannyboy79 said:**
> ok, are any of those partitions mounted? you can tell with teh mount command

```
mount
```

be honest mate i have got a clue.

heres what that command said


> karl@karl-G31-M7-TE:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/karl/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=karl)
/dev/sda2 on /media/Partition_1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
karl@karl-G31-M7-TE:~$

---

### Post by dannyboy79 on 2012-11-13
if your files are not within the /media/Partition_1 folder then mount /dev/sda1 to /mnt/ and see if they are in there. if not, then they must have been deleted andd you might be able to use testdisk or dd_rescue to retrieve deleted files.

---

### Post by taffdragon on 2012-11-13
> **dannyboy79 said:**
> if your files are not within the /media/Partition_1 folder then mount /dev/sda1 to /mnt/ and see if they are in there. if not, then they must have been deleted andd you might be able to use testdisk or dd_rescue to retrieve deleted files.

sorry mate im pretty much clueless with this.

how do i mount something?

and i appreciate your help so far.

edit. i just typed   mount /dev/sda1 to /mnt/  into the terminal and it came back   mount: only root can do that.


another edit. the bit with my windows files on is mounted, at least it say unmount when i hover the mouse over it so im assuming i am mounted. 

is there any way to repair the loader from there? or install a new one maybe?

---

### Post by dannyboy79 on 2012-11-14
so you did or did not find the files you wanted? when it says only root can mount it that means you just need to use "sudo" so it would be
```
sudo mount /dev/sda1 /mnt/
```

---

### Post by taffdragon on 2012-11-17
> **dannyboy79 said:**
> so you did or did not find the files you wanted? when it says only root can mount it that means you just need to use "sudo" so it would be
```
sudo mount /dev/sda1 /mnt/
```


sorry to take so long to get back to you.

i managed to access the vista partion and load vista. managed to get my dvd reader working and ran the vista recovery disk, then command prompt "bootrec/fixboot" and it got me in so i could copy eveything i needed.

thanks a lot for your time and help. i really appreciate it. thank you.

---

