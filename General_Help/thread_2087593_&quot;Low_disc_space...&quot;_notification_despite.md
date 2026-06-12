---
title: "&quot;Low disc space...&quot; notification despite enlarging the disk"
date: 2012-11-24
forum: General Help
---

### Post by varelov on 2012-11-24
Ubuntu 12.10 installed as a guest within Virtual Box 4.2 that keeps complaining about low disc space, despite having the virtual disc image file assigned as dynamicaly expanding.
Granted, I used VBoxManage to enlarge the vdi from 8GB (given by default) to 10GB. The new space is reported by the Disc utility in Ubuntu guest. So, stumbling in the dark, I made it as a new partition, formated it and mounted it by default at /media/my_username.
However, Ubuntu still complains that disk space is too low. What seems to be the problem?

---

### Post by Wim Sturkenboom on 2012-11-24
Please post the results of the commands in red below (3 commands in total)

```

wim@i3-2120:~$ **[COLOR="Red"]df -h[/COLOR]**
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       138G  4,8G  126G   4% /
udev            3,7G  4,0K  3,7G   1% /dev
tmpfs           1,5G  848K  1,5G   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            3,7G  156K  3,7G   1% /run/shm
/dev/sda6       532G   14G  491G   3% /home
/dev/sdc1       925G  210G  706G  23% /mnt/photos
wim@i3-2120:~$ **[COLOR="Red"]sudo du -h --max-depth=1 /[/COLOR]**
[sudo] password for wim: 
14M	/etc
4,0K	/lib64
4,0K	/media
16K	/lost+found
115M	/boot
4,0K	/selinux
0	/sys
210G	/mnt
du: cannot access `/home/wim/.gvfs': Permission denied
14G	/home
44K	/tmp
3,1G	/usr
544K	/root
8,8M	/bin
du: cannot access `/proc/5267/task/5267/fd/3': No such file or directory
du: cannot access `/proc/5267/task/5267/fdinfo/3': No such file or directory
du: cannot access `/proc/5267/fd/3': No such file or directory
du: cannot access `/proc/5267/fdinfo/3': No such file or directory
0	/proc
4,0K	/opt
4,0K	/dev
4,0K	/cdrom
4,0K	/srv
1004K	/run
798M	/lib
680M	/var
8,7M	/sbin
228G	/
wim@i3-2120:~$ **[COLOR="Red"]mount[/COLOR]**
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
/dev/sda6 on /home type ext4 (rw)
/dev/sdc1 on /mnt/photos type ext3 (rw)
gvfs-fuse-daemon on /home/wim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wim)
wim@i3-2120:~$ 

```
For the second command (du), find the largest directory and drill down in it to find subdirectories that are large (in my case /home).

```

wim@i3-2120:~$ **[COLOR="Red"]sudo du -h --max-depth=1 /home[/COLOR]**
16K	/home/lost+found
401M	/home/liza
1,6M	/home/willempie
du: cannot access `/home/wim/.gvfs': Permission denied
14G	/home/wim
14G	/home
wim@i3-2120:~$ 

```
Once you can't find exceptionally large subdirectories, you can use _ls -ls_ (or _ls -lsr_) to find the large files. In my case there is one in /home/wim/VirtualBox VMs/Ubuntu1204_64
```

wim@i3-2120:~$ **[COLOR="Red"]ls -lsr /home/wim/VirtualBox\ VMs/Ubuntu1204_64/[/COLOR]**
total 10485828
10485808 -rw------- 1 wim wim 10737463296 Nov 12 19:45 Ubuntu1204_64.vdi
       8 -rw------- 1 wim wim        7342 Nov  7 16:44 Ubuntu1204_64.vbox-prev
       8 -rw------- 1 wim wim        7342 Nov 12 19:45 Ubuntu1204_64.vbox
       4 drwx------ 2 wim wim        4096 Nov 12 19:34 Logs
wim@i3-2120:~$ 

```

---

### Post by mcduck on 2012-11-24
> **varelov said:**
> Ubuntu 12.10 installed as a guest within Virtual Box 4.2 that keeps complaining about low disc space, despite having the virtual disc image file assigned as dynamicaly expanding.
Granted, I used VBoxManage to enlarge the vdi from 8GB (given by default) to 10GB. The new space is reported by the Disc utility in Ubuntu guest. So, stumbling in the dark, I made it as a new partition, formated it and mounted it by default at /media/my_username.
However, Ubuntu still complains that disk space is too low. What seems to be the problem?

If you added the new space as a new partition, it's not going to add any space on your *existing* partitions, which are the ones running out of space.

So you should either remove the partition you created and instead grow the UBuntu partiton to sue that space, or move some of your personal files to the new partition to free some spacw on the old partition.

---

### Post by varelov on 2012-11-24
Thank you mcduck,I am currently trying to expand the existing partition to the new space via GParted Live (undone formatting so in GParted Live ISO the new space is marked as "unallocated")but the swap is standing in between the partiton that I want to expand and the free space. Am I to delete swap, get gparted to commit the change and then the free space will be available for primary partition to expand?

---

### Post by varelov on 2012-11-24
Ok I think I got it... I guess I didn't understand that the swap is  within an extended partition and that I needed to first expand the extended partition over the unallocated space in order to be able to move the swap to the back. Then I just shrank the extended partition and swap ended up at the end.
Once I did that, the free space became available for primary partition to expand on it.

---

