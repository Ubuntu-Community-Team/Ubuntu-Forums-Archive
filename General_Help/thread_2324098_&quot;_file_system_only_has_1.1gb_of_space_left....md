---
title: "&quot;/ file system only has 1.1gb of space left...&quot; what do I do?"
date: 2016-05-10
forum: General Help
---

### Post by nzdreamer55 on 2016-05-10
I have been getting a message that tells me that the / only has 1/1gb of space left.  I am new to Linux from a windows world and don't really know how to look to free up space.  I have a 64gb SSD for my OS and am running Ubuntu 14.04 on an older laptop.  I do have a USB drive that I use for storage and this is where all my files should be going to keep the SSD free.

How do I check what might be taking up all the space and then how do I know if I can delete stuff?

Thanks

---

### Post by QDR06VV9 on 2016-05-10
First see if this is the problem
```
sudo apt-get autoremove
```
And post back the output of this in the terminal
```
df -h
```

---

### Post by RobGoss on 2016-05-10
You can also try this handy tool **[Disk usage analyzer]("https://apps.ubuntu.com/cat/applications/natty/baobab/") **it will provide a graphical view of everything on your system that uses your disk space

> 
[COLOR=#000000]How do I check what might be taking up all the space and then how do I know if I can delete stuff?[/COLOR]

As far as deleting stuff I would make sure you know what everything is before you start deleting anything this may cause you yet other problems with your system

[h=1][/h]

---

### Post by nzdreamer55 on 2016-05-10
Thanks for the support.

Here is the output

```
linux@linuxlaptop:~$ sudo apt-get autoremove[sudo] password for linux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libjansson4 libntdb1 linux-headers-4.2.0-27 linux-headers-4.2.0-27-generic
  linux-image-4.2.0-27-generic linux-image-extra-4.2.0-27-generic python-ntdb
0 upgraded, 0 newly installed, 7 to remove and 8 not upgraded.
After this operation, 295 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 292077 files and directories currently installed.)
Removing libjansson4:amd64 (2.5-2) ...
Removing python-ntdb (1.0-2ubuntu1) ...
Removing libntdb1:amd64 (1.0-2ubuntu1) ...
Removing linux-headers-4.2.0-27-generic (4.2.0-27.32~14.04.1) ...
Removing linux-headers-4.2.0-27 (4.2.0-27.32~14.04.1) ...
Removing linux-image-extra-4.2.0-27-generic (4.2.0-27.32~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-35-generic
Found initrd image: /boot/initrd.img-4.2.0-35-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found initrd image: /boot/initrd.img-4.2.0-30-generic
Found linux image: /boot/vmlinuz-4.2.0-27-generic
Found initrd image: /boot/initrd.img-4.2.0-27-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-4.2.0-27-generic (4.2.0-27.32~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
update-initramfs: Deleting /boot/initrd.img-4.2.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-27-generic /boot/vmlinuz-4.2.0-27-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-35-generic
Found initrd image: /boot/initrd.img-4.2.0-35-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found initrd image: /boot/initrd.img-4.2.0-30-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...

linux@linuxlaptop:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         986M   12K  986M   1% /dev
tmpfs                        200M  1.3M  198M   1% /run
/dev/dm-0                     57G   52G  1.7G  97% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
none                         5.0M     0  5.0M   0% /run/lock
none                         996M  9.3M  987M   1% /run/shm
none                         100M   44K  100M   1% /run/user
/dev/sda1                    236M  101M  123M  46% /boot
//192.168.1.170/Series.Pool   16T   15T  1.4T  92% /home/linux/mnt/Series.Pool
//192.168.1.170/Film.Pool     11T  9.8T  1.2T  90% /home/linux/mnt/Film.Pool
//192.168.1.170/Om           3.7T  2.2T  1.6T  59% /home/linux/mnt/Om
/dev/sdb1                    932G  508G  424G  55% /media/linux/1TB.Scratch

```





So the network drives I am not worried about as these I manage else where.  The 1TB.Scratch is were I D/L stuff that gets moved to the networked drives.

Wish I had a screen shot of the exact error message.

Thanks again for the help

---

### Post by QDR06VV9 on 2016-05-10
Have you checked and emptied the trash?

---

### Post by qyot27 on 2016-05-10
```
cd /
du -h --max-depth 1
```

That will show the breakdown of where the space is being consumed.  If it's /home or /opt, then I'd consider migrating those to dedicated partitions on an external drive.

---

### Post by grahammechanical on 2016-05-10
> /dev/dm-0                     57G   52G  1.7G  97% /

That is your situation. dm-0 is the name of your installation of Ubuntu and it is on a partition that is 57GB in size but 52GB is used. There will be a /home/username folder and in there somewhere will be other folders with large files. That is my guess.

The file manager will open at /home/username/home. In the left hand pane there will be locations; Home; Desktop; Documents; Downloads; Music; Pictures; Videos; Rubbish Bin. Select each location in turn and right click it and then select Properties. The dialog will tell you how much space is being used in each folder. The exception to this is the Rubbish Bin. But it is the right click on the Rubbish Bin that will give us the option to empty it.

Regards
Regards.

---

### Post by nzdreamer55 on 2016-05-11
Again thanks for the help.

I emptied the trash (only one empty folder) and looked at all the folders under the "Places" within the file browser.  Under Home, Desktop, Documents, Music, Pictures, Video it showed Free space of 1.7 GB.  with nothing within these folders.  My Downloads folder contains 118 items totaling 711.5 MB.

So is my 64GB OS drive too small for Ubuntu?  It fit windows 8.1 with about 20 GB of free space to spare.

And for the person who recommending running the following command (du -h --max-depth 1) here is the output but it has hung and I have to <ctrl>-C to stop it.

```
linux@linuxlaptop:/$ sudo du -h --max-depth 1[sudo] password for linux: 
4.0K    ./cdrom
1.1G    ./var
4.0K    ./mnt
4.0K    ./lib64
13M    ./sbin
509G    ./media
du: cannot access ‘./proc/19036/task/19036/fd/4’: No such file or directory
du: cannot access ‘./proc/19036/task/19036/fdinfo/4’: No such file or directory
du: cannot access ‘./proc/19036/fd/3’: No such file or directory
du: cannot access ‘./proc/19036/fdinfo/3’: No such file or directory
0    ./proc
64K    ./tmp



```

---

### Post by leunam12 on 2016-05-11
Use the Disk Usage Analyzer utility, it will let you see graphically what's eating up the space. I run Ubuntu (/) on a 24GB partition and it's never more than 32% full. A 64GB is more than enough if you move your videos and music (and other large files) to your storage drive.

---

### Post by QDR06VV9 on 2016-05-11
> **grahammechanical said:**
> _**That is your situation. dm-0 is the name of your installation of Ubuntu and it is on a partition that is 57GB in size but 52GB is used**_. There will be a /home/username folder and in there somewhere will be other folders with large files. That is my guess.

The file manager will open at /home/username/home. In the left hand pane there will be locations; Home; Desktop; Documents; Downloads; Music; Pictures; Videos; Rubbish Bin. Select each location in turn and right click it and then select Properties. The dialog will tell you how much space is being used in each folder. The exception to this is the Rubbish Bin. But it is the right click on the Rubbish Bin that will give us the option to empty it.

Regards
Regards.
+1 Good Advice:)

---

### Post by Impavidus on 2016-05-11
> **nzdreamer55 said:**
> Again thanks for the help.

I emptied the trash (only one empty folder) and looked at all the folders under the "Places" within the file browser.  Under Home, Desktop, Documents, Music, Pictures, Video it showed Free space of 1.7 GB.  with nothing within these folders.  My Downloads folder contains 118 items totaling 711.5 MB.

So is my 64GB OS drive too small for Ubuntu?  It fit windows 8.1 with about 20 GB of free space to spare.It isn't too small. Ubuntu should take about 10GB. So something is going on.

> And for the person who recommending running the following command (du -h --max-depth 1) here is the output but it has hung and I have to <ctrl>-C to stop it.

(...)
That command just takes a long time to run. I think it was busy analysing the stuff in /home/linux/mnt/, which would have taken ages and would be quite useless. We can prevent that with an option (-x) to stay on one filesystem only:```
sudo du -xh --max-depth 1 /
```

---

### Post by nzdreamer55 on 2016-05-20
Thanks for the ideas.  So I was able to run disk analyzer as a su and took a screen shot.  It looks like my root partition only has 7GB of space.  Is this correct?

---

### Post by leunam12 on 2016-05-21
post the results of lsblk.

---

### Post by Impavidus on 2016-05-21
> **nzdreamer55 said:**
> Thanks for the ideas.  So I was able to run disk analyzer as a su and took a screen shot.  It looks like my root partition only has 7GB of space.  Is this correct?

No, it indicates you have 7.7GB of disk space in your root partition in use. Disk usage analyser doesn't tell how the size of your root partition. The percentages show the size of each directory as a percentage of its parent directory, so the root directory is always at 100%.

Maybe you have some files hidden in directories used as a mount point for your network drive or your 1TB.Scratch. You may have attempted to copy files to those file systems while they were unmounted, which would have resulted in the files ending up on your root partition, hidden from view as soon as the other partitions were mounted. You can check this by unmounting those partitions and making sure the directories acting as mountpoints are empty.

---

### Post by nzdreamer55 on 2016-05-21
linux@linuxlaptop:~$ lsblk
NAME                         MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                            8:0    0  59.6G  0 disk 
&#9500;&#9472;sda1                         8:1    0   243M  0 part /boot
&#9500;&#9472;sda2                         8:2    0     1K  0 part 
&#9492;&#9472;sda5                         8:5    0  59.4G  0 part 
  &#9500;&#9472;ubuntu--vg-root (dm-0)   252:0    0  57.4G  0 lvm  /
  &#9492;&#9472;ubuntu--vg-swap_1 (dm-1) 252:1    0     2G  0 lvm  [SWAP]
sdb                            8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1                         8:17   0 931.5G  0 part /media/linux/1TB.Scratch

---

### Post by nzdreamer55 on 2016-05-21
> **Impavidus said:**
> No, it indicates you have 7.7GB of disk space in your root partition in use. Disk usage analyser doesn't tell how the size of your root partition. The percentages show the size of each directory as a percentage of its parent directory, so the root directory is always at 100%.

Maybe you have some files hidden in directories used as a mount point for your network drive or your 1TB.Scratch. You may have attempted to copy files to those file systems while they were unmounted, which would have resulted in the files ending up on your root partition, hidden from view as soon as the other partitions were mounted. You can check this by unmounting those partitions and making sure the directories acting as mountpoints are empty.

So my mount points may contain files that are hidden on my root drive that are hidden?  Wow.  I would have never thought that this could happen.

So is there a way to

1) list the mount points for other drives than my hard drive that ubuntu is on?
2) show hidden files on these mount points?

---

### Post by nzdreamer55 on 2016-05-21
BTW her is output from df

linux@linuxlaptop:~$ df
Filesystem                                   1K-blocks        Used  Available                           Use% Mounted on
udev                                                   1008352           4    1008348                            1% /dev
tmpfs                                                    203956        1224     202732                          1% /run
/dev/dm-0                                         59101340    54989916    1086120                    99% /
none                                                               4           0          4                                  0% /sys/fs/cgroup
none                                                         5120           0       5120                               0% /run/lock
none                                                    1019776        8300    1011476                        1% /run/shm
none                                                      102400          60     102340                           1% /run/user
/dev/sda1                                               240972      135856      92675                      60% /boot
//192.168.1.170/Series.Pool         18557774828 15002003340 3555771488            81% /home/linux/mnt/Series.Pool
//192.168.1.170/Film.Pool            11720656884 10528344536 1192312348            90% /home/linux/mnt/Film.Pool
//192.168.1.170/Om                       3906885628  2339563360 1567322268             60% /home/linux/mnt/Om
//192.168.1.104/OffLineStorage     1918212624   853194100 1064916124              45% /home/linux/mnt/Diskstation
/dev/sdb1                                         976758904   126922228  849836676                13% /media/linux/1TB.Scratch

---

### Post by nzdreamer55 on 2016-05-21
> **Impavidus said:**
> It isn't too small. Ubuntu should take about 10GB. So something is going on.


That command just takes a long time to run. I think it was busy analysing the stuff in /home/linux/mnt/, which would have taken ages and would be quite useless. We can prevent that with an option (-x) to stay on one filesystem only:```
sudo du -xh --max-depth 1 /
```


That was much faster :-)  Here is the output from that.

---

### Post by nzdreamer55 on 2016-05-24
Hello????  I had so many people respond and now it is kind of empty.  :`-(

---

### Post by Impavidus on 2016-05-25
I'm sorry, I'll elaborate on my previous suggestion.

It's clean now that the visible files don't account for all used disk space, so there must be hidden files.

You can use```
mount
```to get a list of your mounted partitions. It will show you the mountpoints. Use```
sudo umount <mount point>
```to unmount them. Note the command is umount, not unmount. Don't bother with the automatically mounted systems on /sys, /run etc. From one of your earlier posts, it must be about /media/linux/1TB.Scratch, /home/linux/mnt/Diskstation, /home/linux/mnt/Om, /home/linux/mnt/Film.Pool and /home/linux/mnt/Series.Pool. Then use the file manager or terminal or whatever you prefer to look at the mountpoint. It should now be an empty directory. If there are files in it, those are the hidden (but now unhidden) files using all your disk space.

Move the files somewhere else. The easiest way is to rename the directory where you find them and then recreate the original, for example```
mv /home/linux/mnt/Film.Pool /home/linux/mnt/Film.Pool.old
mkdir /home/linux/mnt/Film.Pool
```If you normally mount those partitions with fstab, you can remount them using```
sudo mount -a
```Else, remount them in the way you prefer. Then move the files to the place where they belong. Or delete them, if they appear to be duplicates.

---

### Post by nzdreamer55 on 2016-05-25
Thanks for the help!  I though I was lost after the delay in response :-)  Really appreciate it.  So here is the output of mount

```
linux@linuxlaptop:~$ mount/dev/mapper/ubuntu--vg-root on / type ext4 (rw,errors=remount-ro)
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
/dev/sda1 on /boot type ext2 (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=linux)
//192.168.1.170/Series.Pool on /home/linux/mnt/Series.Pool type cifs (rw,username=*,password=*,iocharset=utf8,uid=1000,gid=1000,file_mode=0770,dir_mode=0770,noperm)
//192.168.1.170/Om on /home/linux/mnt/Om type cifs (rw,username=***,password=***,iocharset=utf8,uid=1000,gid=1000,file_mode=0770,dir_mode=0770,noperm)
//192.168.1.170/Film.Pool on /home/linux/mnt/Film.Pool type cifs (rw,username=*,password=*,iocharset=utf8,uid=1000,gid=1000,file_mode=0770,dir_mode=0770,noperm)
//192.168.1.104/OffLineStorage on /home/linux/mnt/Diskstation type cifs (rw,username=***,password=***,iocharset=utf8,uid=1000,gid=1000,file_mode=0770,dir_mode=0770,noperm)
/dev/sdb1 on /media/linux/1TB.Scratch type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

```

I think I want to start with my 1TB.Scratch disk.  This is a usb drive attached to my computer.

So do I umount /dev/sdb1 or umount /media/linux/1TB.Scratch

---

### Post by Impavidus on 2016-05-25
> **nzdreamer55 said:**
> 
So do I umount /dev/sdb1 or umount /media/linux/1TB.Scratch

It's supposed to work both ways, as this partition is only mounted at one place. I suggest the second version.

---

### Post by nzdreamer55 on 2016-05-25
Thanks again.  So here is what happened.

```
linux@linuxlaptop:~$ umount /media/linux/1TB.Scratchumount: /media/linux/1TB.Scratch is not in the fstab (and you are not root)
linux@linuxlaptop:~$ sudo umount /media/linux/1TB.Scratch
[sudo] password for linux: 
linux@linuxlaptop:~$ cd /media/linux/1TB.Scratch
bash: cd: /media/linux/1TB.Scratch: No such file or directory
linux@linuxlaptop:~$ 

```

So from there I opened my files from the explorer (that is what it is called in windows) and when I navigated to the 1TB.Scratch drive, the drive spun up, and I see that there are the same files present.  See the picture below.  So I don't know if I umounted the drive correctly.  It seems like I did from the terminal and I could not get to the drive to see if there were hidden files on it but when I went to look for hidden files through the Explorer, it seemed like it mounted the drive again.

Was I suppose to check some where else for the hidden files?

---

### Post by nzdreamer55 on 2016-05-25
Ok so I re-read what you posted and figured it out.  There were files under my Series.Pool that were "hidden".  Deleted these and remounted and now only about 7gb are on the OS drive!!!!!

THANK YOU SO MUCH :-)

---

### Post by Impavidus on 2016-05-26
Great. Could you mark this thread as solved? Top of page, click "thread tools" -> "mark as solved".

---

### Post by nzdreamer55 on 2016-05-26
You bet!

Done!

---

