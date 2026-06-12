---
title: "Hard disk space Problems.  **PLEASE HELP**"
date: 2013-05-13
forum: General Help
---

### Post by braedentraut24 on 2013-05-13
I have ChrUbuntu 12.04 for ChromeOS.  When installing Ubuntu I gave my laptop 10 GB of memory.  I then realized that that was not enough after installing different programs.  I don't understand why it says I don't have enough space when I have a 305 GB Hard Drive.  I mounted that and everything but it didn't work.  I tried to repartition my disk but that didn't work either.  I also wiped my computer, did a powerwash in ChromeOS then reinstalled Ubuntu, but it did not ask me for a memory amount.  I have tried really everything in my power to try to get more memory but I honestly can't.  Could someone explain to me how I could get that memory back like I'm a VERY stupid person.  I know tons about computers and I'm good at terminal (just not reading the help sections, I just can't do it its too confusing) and I can edit files pretty well and I know my way around.  Could someone please help me?

---

### Post by papibe on 2013-05-13
Hi raedentraut24.

Could you open a terminal, and post the results of these commands?
```
df -h

df -i

sudo fdisk -l

mount -l
```
Regards.

---

### Post by braedentraut24 on 2013-05-13
Ok this is what I got.  Im not really sure how to read this though.  
```
user@ChrUbuntu:~$ df -hFilesystem      Size  Used Avail Use% Mounted on
/dev/sda7        10G  5.4G  4.2G  56% /
devtmpfs        2.9G  4.0K  2.9G   1% /dev
none            590M  684K  590M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.9G  496K  2.9G   1% /run/shm
/dev/sda1       284G  5.9G  264G   3% /media/1eac4742-c969-42c8-9020-1ec2d7fde39d
user@ChrUbuntu:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda7        655360 224773   430587   35% /
devtmpfs         754716    469   754247    1% /dev
none             755033    468   754565    1% /run
none             755033      3   755030    1% /run/lock
none             755033      7   755026    1% /run/shm
/dev/sda1      18612224     88 18612136    1% /media/1eac4742-c969-42c8-9020-1ec2d7fde39d
user@ChrUbuntu:~$ sudo fdisk -l
[sudo] password for user: 


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 320.1 GB, 320072933376 bytes
256 heads, 63 sectors/track, 38761 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   625142447   312571223+  ee  GPT
Partition 1 does not start on physical sector boundary.
user@ChrUbuntu:~$ mount -l
/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
devtmpfs on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/user/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=user)
/dev/sda1 on /media/1eac4742-c969-42c8-9020-1ec2d7fde39d type ext4 (rw,nosuid,nodev,uhelper=udisks)
user@ChrUbuntu:~$ 

```

---

### Post by oldos2er on 2013-05-14
I've changed your thread title a bit since your question is about hard disk space, not [memory]("http://en.wikipedia.org/wiki/Random-access_memory").

---

### Post by papibe on 2013-05-15
You still have 4.2G available on your root partition. That's enough for lots of software.

I would recommend:
[LIST]
[*]migrate your home to the /dev/sda1 partition, and then mount it as /home, and
[*]using a live media, like the Ubuntu installation CD/USB, increase the size of the root partition to something like 25G.
[/LIST]
Let us know if you need more help with that.
Regards.

---

