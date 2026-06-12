---
title: "Not able to delete files from Transcend 8gb flash drive"
date: 2017-05-19
forum: General Help
---

### Post by ronnie.s on 2017-05-19
I'm not able to delete files from my Transcend 8 gb flash drive. I'm not able to change permissions of files either. 

I had formatted it into FAT32 filesystem using Gparted. After this I was able to copy files into it, but I am not able to delete anything. I am not even able to delete the partition using Gparted.

---

### Post by ajgreeny on 2017-05-19
Does it have a small physical Read-only slide or switch?

With it attached and mounted what does the **mount** command output?

---

### Post by ronnie.s on 2017-05-19
> **ajgreeny said:**
> Does it have a small physical Read-only slide or switch?

With it attached and mounted what does the **mount** command output?

It does not seem to have a switch or a slide. 

I don't understand your question " .... what does the mount command output?" When I plug it in, a folder opens and displays the files in it. I tried almost everything that I could think of, trying to delete the files as root, trying to change the permissions, trying to format the flash drive using gparted. Nothing seems to work. Every time I get the error that it can only be read. 

Perhaps there is a command to mount it in such a way that one can also write to it. Any ideas? 

Thanks.

---

### Post by coffeecat on 2017-05-19
What ajgreeny was asking you was to run the mount command in a terminal and post the output, which will give useful information about how the USB drive is mounted.

So. Open a terminal and run this command:

```
mount
```

You will get a few lines of output, only one of which is relevant, but please post the whole output. Don't try to retype the output into your post. You can copy and paste it by highlighting the output with the mouse -> right-click -> Copy. Then paste (ctrl-v) the output into your post. Please enclose the pasted output between [noparse]```
 and 
```[/noparse] tags for readability and to preserve formatting.

---

### Post by ronnie.s on 2017-05-19
```


$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4015812k,nr_inodes=1003953,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=807212k,mode=755)
/dev/sda4 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=24,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda5 on /home type ext4 (rw,relatime,data=ordered)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda6 on /Ronnie type vfat (rw,relatime,gid=46,fmask=0007,dmask=0007,allow_utime=0020,codepage=437,iocharset=iso8859-1,shortname=mixed,utf8,errors=remount-ro)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=807212k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdb1 on /media/ronnie/B2C6-0E24 type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)


```

The last line is the relevant one, that is, the one "/dev/sdb1 on ....".

---

### Post by coffeecat on 2017-05-19
Indeed it is. 

I can't see anything that would explain why you can't delete stuff on it. It's mounted read-write. By the way, you can't change permissions of files on a Microsoft filesystem, which is what FAT32 is. The permissions are set by the mount options.

Please elaborate on what you mean by "not able to delete anything". Were you using a GUI file browser and, if so, what exactly did you try to do, and what error message, if any, did you see? Or were you using the terminal?

Also, what happened when you tried to delete the partition using Gparted? My guess is that the partition was still mounted. It has to be unmounted for Gparted to be able to delete it. I doubt whether deleting the partition would have helped you in any way, but it would be of value to know what happened.

---

### Post by The Cog on 2017-05-19
It looks as though it is mounted on /media/ronnie/B2C6-0E24. It is mounted read-write, so ronnie should be able to delete the files. 
How are you trying to delete them?

Can you open a terminal in the drive and run the command 
```
ls -l | head
```
and post the output. That should tell us about the apparent file permissions. You won't be able to change many permissions or change the ownership because it's a FAT filesystem that cannot store them, but you should be able to change the read-only flag.

I am not sure that root would be allowed to delete them, because the drive has been auto-mounted for ronnie. EDIT: trial & error here, yes root can delete them.
Also, while the drive is mounted, you cannot format it - it is in use. Unmount it before trying to format it.

---

### Post by ronnie.s on 2017-05-19
The whole purpose of creating a FAT32 file system was thinking that I would be able to read the files in Windows as well (this was a terrible decision since I rarely use windows).

I was being really careless and hasty while using Gparted, and I don't really remember what I did. But something screwed up. I wonder if there is some problem with the pen drive. 

ls -al gives the output 

-rw-r--r--

and in the terminal the command

sudo chmod 777 * 

does nothing. So I really don't understand what is going on. Does this response answer your question? If you want more details, I'll be happy to post outputs of commands I give on the terminal.

```
ls -l | head
```

outputs only a few of the files 

```


ls -l | head
total 52
drwxr-xr-x 7 ronnie ronnie 24576 May 20 02:42 Books
drwxr-xr-x 2 ronnie ronnie 28672 May 19 23:03 Papers


```

If I change directory to Books and give the command

```


ls -al


```

Then I a get the whole list of books. But in the same directory giving the command 

```


ls -l | head 


```

lists only the first few, the precise output being

```

 ls -l | head
total 985904
-rw-r--r-- 1 ronnie ronnie  3418634 Aug  8  2016 AlgOslo.djvu
-rw-r--r-- 1 ronnie ronnie  3751026 Aug  8  2016 AlgTokyo1982.djvu
-rw-r--r-- 1 ronnie ronnie  1045579 Aug  8  2016 AltTheory.djvu
-rw-r--r-- 1 ronnie ronnie  2436591 Aug  8  2016 An.djvu
-rw-r--r-- 1 ronnie ronnie  5038298 Aug  8  2016 ArCurves.djvu
-rw-r--r-- 1 ronnie ronnie   372701 Aug  8  2016 ArtSaces.djvu
drwxr-xr-x 2 ronnie ronnie     4096 May 19 23:05 ArTopologies
-rw-r--r-- 1 ronnie ronnie  1630194 May 19 23:06 Ash.pdf
-rw-r--r-- 1 ronnie ronnie  1672440 Aug  8  2016 AtAlgebra.djvu



```

With the flash drive unmounted I started the graphical interface of GParted and try to delete the partition. 

I get an error saying "Can't write to /dev/sdb as it is opened read-only".

---

### Post by The Cog on 2017-05-19
Yes, head only prints the first ten lines passing through it by default - I didn't want you getting a list hundreds of lines wrong - the first ten is enough to see what's up. Nothing is up, it all looks normal.

Can you change into that directory again and use the command 
```
rm AlgOslo.djvu
```
Let's see if the file gets deleted or if there is a helpful error message.

EDIT: also, that gparted message looks odd. Can you post the output of
```
ls -l /dev/sd*
```

---

### Post by ronnie.s on 2017-05-19
This is really strange. When I give the command 
```
 rm AlgOslo.djvu 
```
There is no error message. On giving 
```
ls
```
I see that the file is still there.

The output of 
```
 ls -l /dev/sd*
```
is 
```
ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 May 20 03:09 /dev/sda
brw-rw---- 1 root disk 8,  1 May 20 03:09 /dev/sda1
brw-rw---- 1 root disk 8,  2 May 20 03:09 /dev/sda2
brw-rw---- 1 root disk 8,  3 May 20 03:09 /dev/sda3
brw-rw---- 1 root disk 8,  4 May 20 03:09 /dev/sda4
brw-rw---- 1 root disk 8,  5 May 20 03:09 /dev/sda5
brw-rw---- 1 root disk 8,  6 May 20 03:09 /dev/sda6
brw-rw---- 1 root disk 8,  7 May 20 03:09 /dev/sda7
brw-rw---- 1 root disk 8,  8 May 20 03:09 /dev/sda8
brw-rw---- 1 root disk 8, 16 May 20 03:11 /dev/sdb
brw-rw---- 1 root disk 8, 17 May 20 03:10 /dev/sdb1

```

---

### Post by The Cog on 2017-05-19
Hmm. That is odd. The kind of thing that sends people running away screaming. 

How about the output from 
```
ls -l /dev/sd*
```

Maybe the device driver is read-only for some reason? ??? :confused:

---

### Post by ronnie.s on 2017-05-19
```

ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 May 20 03:09 /dev/sda
brw-rw---- 1 root disk 8,  1 May 20 03:09 /dev/sda1
brw-rw---- 1 root disk 8,  2 May 20 03:09 /dev/sda2
brw-rw---- 1 root disk 8,  3 May 20 03:09 /dev/sda3
brw-rw---- 1 root disk 8,  4 May 20 03:09 /dev/sda4
brw-rw---- 1 root disk 8,  5 May 20 03:09 /dev/sda5
brw-rw---- 1 root disk 8,  6 May 20 03:09 /dev/sda6
brw-rw---- 1 root disk 8,  7 May 20 03:09 /dev/sda7
brw-rw---- 1 root disk 8,  8 May 20 03:09 /dev/sda8
brw-rw---- 1 root disk 8, 16 May 20 03:11 /dev/sdb
brw-rw---- 1 root disk 8, 17 May 20 03:10 /dev/sdb1

```

Maybe I should have mentioned this. I had initially made my flash drive into a bootable usb with Xubuntu. Once I installed Xubuntu on my laptop, I decided I will make the flash drive into a FAT32 file system. I was successfully able to do this using GParted. I copied some files into the flash drive. But after transferring these files to another computer, I was not able to delete them any more. That was when I realized the problem.

---

### Post by The Cog on 2017-05-19
Yes, I'm a slow typist, we're crossing messages. Oh well. Not a problem.
/dev/sdb is read-write for root. That's what I expect. 

I'm running short of ideas. Two possibilities that I would try in this order:
1: Mount the drive elsewhere as well, and try to delete files from there:
```
sudo mkdir /media/xxx
sudo mount /dev/sda1 /media/xxx
cd /media/xxx/Books
rm  AlgOslo.djvu
ls
```
then clean up:
```
cd /
umount /media/xxx
rmdir /media/xxx
```

2: Unmount the drive and wipe the partition table:
Right click the drive icon and unmount (not eject) it.
Make very sure you get the right device here or you could wipe your main drive:
```
sudo dd if=/dev/zero of=/dev/sdb bs=1M count=1
sync
```

---

### Post by ronnie.s on 2017-05-19
> **The Cog said:**
> Yes, I'm a slow typist, we're crossing messages. Oh well. Not a problem.
/dev/sdb is read-write for root. That's what I expect. 

I'm running short of ideas. Two possibilities that I would try in this order:
1: Mount the drive elsewhere as well, and try to delete files from there:
```
sudo mkdir /media/xxx
sudo mount /dev/sda1 /media/xxx
cd /media/xxx/Books
rm  AlgOslo.djvu
ls
```
then clean up:
```
cd /
umount /media/xxx
rmdir /media/xxx
```



When I do the above, sometimes I get an error saying that the files cannot be deleted, whereas at other times even after the command runs the files are still there. 

> 

2: Unmount the drive and wipe the partition table:
Right click the drive icon and unmount (not eject) it.
Make very sure you get the right device here or you could wipe your main drive:
```
sudo dd if=/dev/zero of=/dev/sdb bs=1M count=1
sync
```

What is I just wipe the partition table without doing step 1? What will be the effect of that?

I now also tried deleting the files using windows. There too I get the same error saying that the files are readonly. There too I could not delete the partition using the command "attributes disk clean readonly". Does this mean that my pen drive is damaged?

Some more updates: I mounted /dev/sdb1 at /media/test
It turns out that I can write files into the directory /media/test and I can also delete any new files I write here. However, I cannot write anything into the directory /media/test/Books
However, at this stage all the files are shown to be owned by root and have permissions "-rwxr-xr-x" which is better than what it was earlier (-rw-r--r--).

---

### Post by The Cog on 2017-05-20
Hmm. I wonder if it is as simple as the directory Books being read-only. That would mean you can't write to the directory, so you can't change its contents. 
**ls -l /media/test**
and look at the permissions on the directory Books. However, I suspect that's not it because I would expect a permission denied error when you try to delete the contents. Sorry, but I think maybe the flash drive is damaged.

---

### Post by ronnie.s on 2017-05-20
Yes. I too think that my flash drive is damaged.

---

### Post by ajgreeny on 2017-05-20
Assuming you have backups or copies of all the files on that drive can you try making a new partition table using gparted.

Right click on the current partition to make sure it's unmounted then go to **Device ->Create partition table**, accept the default msdos table and when that finishes create a new partition in the now unallocated space.

I know we have tried similar actions before but like all the other helpers, this seems a very strange situation so anything is worth trying.

---

### Post by ronnie.s on 2017-05-21
When I try to create a partition table, it gives a prompt "Can't write to /dev/sdb, because it is openend read-only". From here I cannot proceed!

---

### Post by Dennis N on 2017-05-21
Usually, making a new partition table from gparted works to "recover" a usb that had been used as an installer made with a tool using dd. But, I do recall one instance where gparted failed to fix things, and resorting to gdisk did the job. Maybe worth a try.

---

### Post by ajgreeny on 2017-05-21
last resort; try [mkusb]("https://help.ubuntu.com/community/mkusb") which can usually "mend" a USB that has been apparently broken in this way and restore it to normal mass-storage use , though, of course, if the drive really is dead this will not help to get it running again.

---

### Post by ronnie.s on 2017-05-22
I tried somethings with gdisk. Mounted my flash drive, deleted all the stuff in it, unmounted it, to see that all the files are still there. I guess it's safe to assume that the drive is damaged.

---

