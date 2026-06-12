---
title: "[SOLVED] No space left on device for root"
date: 2008-01-02
forum: General Help
---

### Post by arunsub on 2008-01-02
My '/' partition suddenly got full. I'm not sure what caused it to fill up. The only thing I use newly (for the past 2 weeks) is the **Simple Backup**. I thought that was the culprit, so I checked the /var/backups and it is only few MBs. I have allocated 9.6 GB for '/'. Here are some outputs.

**df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             9.7G  9.7G     0 100% /
varrun                506M  220K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  148K  506M   1% /proc/bus/usb
udev                  506M  148K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda5             1.5G   52M  1.4G   4% /boot
/dev/sda8              22G   11G   11G  50% /home
/dev/sda1              40G  9.7G   30G  25% /media/sda1
/dev/sda9              80G   63G   17G  80% /media/sda9
overflow              1.0M  196K  828K  20% /tmp
/dev/sdb1             466G   54G  413G  12% /media/OneTouch4_

**sudo du -sh /***
4.8M    /bin
18M     /boot
0       /cdrom
160K    /dev
11M     /etc
11G     /home
4.0K    /initrd
0       /initrd.img
158M    /lib
16K     /lost+found
79G     /media
4.0K    /mnt
163M    /opt
0       /proc
11M     /root
6.5M    /sbin
4.0K    /srv
0       /sys
196K    /tmp
2.4G    /usr
250M    /var
0       /vmlinuz

**mount**
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda5 on /boot type ext3 (rw)
/dev/sda8 on /home type ext3 (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda9 on /media/sda9 type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/OneTouch4_ type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

Any help is greatly appreciated.

---

### Post by theheadlessrabbit on 2008-01-02
I've run into exactly the same problem just yesterday.

has your systems boot time been affected?

mine takes about a minute longer to load since the data mysteriously appeared on my HD.

---

### Post by sciencewhiz on 2008-01-02
try booting from your install disk and running a file system check on sda6

```
fsck  -f /dev/sda6 
```

---

### Post by arunsub on 2008-01-03
sciencewhiz, I'll try that when I get home today and update the post. 
theheadlessrabbit, I didn't pay close attention to the boot time. I thought it took a minute longer, but not sure.

---

### Post by arunsub on 2008-01-03
Here is the fsck output for /dev/sda6
 fsck -f /dev/sda6
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda6: 130125/1281696 files (0.9% non-contiguous), 2557782/2560351 blocks

---

### Post by arunsub on 2008-01-05
Help please!!!

---

### Post by geraldm on 2008-01-07
One thing is certain when the root partition is full.  You will not be able to boot until you have created some room on the root partition.  I do not know how much is needed, but when that happened to me, I took out 1 megabyte.  If /var/log is in the root partition, look for logfiles that are no longer important; if /home is in the root partition, look for files you would not miss and
unload them.  Unimportant programs could be removed without missing them if you can later install them from the install disk or the internet.

Gerald

---

### Post by arunsub on 2008-01-07
Is there a way to find out which files (not directories) are taking max bytes under the / partition? /home has it's own parition.

---

### Post by forestpixie on 2008-01-07
Can't answer the question  and not sure if it works - can you boot to recovery if so run

sudo apt-get clean

it'll clear the apt cache

I'm not sure if deleting the cache from the livecd is a good idea


if you've got stuff in trash you should be able to get to it from the livecd - maybe there's enough in there to be able to start

---

### Post by forestpixie on 2008-01-07
just a thought - do you have a separate /boot partition or do you just have /

I think you need to free room in the /boot directory - if you have more than one kernel in there, perhaps deleting the old one will be sufficient to get it started in order to clean up elsewhere

Edit - from [this]("http://ubuntuforums.org/showthread.php?t=479405") thread - there is this

> boot the live cd, chroot (please google or use ubuntu forum search if you don't know how to do this) into your ubuntu installation, then do
sudo aptitude autoclean
sudo aptitude clean

this will remove unnessessary packages from your apt cache. according to the man pagaes for aptitude clean and autoclean:
clean

This thread gives some idea of how to do ti
[http://ubuntuforums.org/showthread.php?t=157250](http://ubuntuforums.org/showthread.php?t=157250)

---

### Post by geirha on 2008-01-07
What's the output of this? ```
du --max-depth=1 -xh /
```

---

### Post by vanadium on 2008-01-08
Indeed, run the du command from a live CD with no partitions mounted except your problem partition that is full. Then du will only report on that. Also, you might want to sort:

du --max-depth=1 | sort -rn | less

This should show you where the space is going. Check wether the total reported agrees (more or less) with the total space on your disk.

---

### Post by arunsub on 2008-01-08
> **forestpixie said:**
> Can't answer the question  and not sure if it works - can you boot to recovery if so run

sudo apt-get clean

it'll clear the apt cache

I'm not sure if deleting the cache from the livecd is a good idea


if you've got stuff in trash you should be able to get to it from the livecd - maybe there's enough in there to be able to start

I tried those. It didn't clear much.

---

### Post by arunsub on 2008-01-08
> **forestpixie said:**
> just a thought - do you have a separate /boot partition or do you just have /

I think you need to free room in the /boot directory - if you have more than one kernel in there, perhaps deleting the old one will be sufficient to get it started in order to clean up elsewhere

Edit - from [this]("http://ubuntuforums.org/showthread.php?t=479405") thread - there is this



This thread gives some idea of how to do ti
[http://ubuntuforums.org/showthread.php?t=157250](http://ubuntuforums.org/showthread.php?t=157250)

I have separate partitions for '/boot','/' and '/home'. The problem is with '/' partition. Boot is fine.

---

### Post by arunsub on 2008-01-08
> **vanadium said:**
> Indeed, run the du command from a live CD with no partitions mounted except your problem partition that is full. Then du will only report on that. Also, you might want to sort:

du --max-depth=1 | sort -rn | less

This should show you where the space is going. Check wether the total reported agrees (more or less) with the total space on your disk.

Geirha & Vanadium, I'll try that. How do I just mount '/' partition without mounting other partitions from the live CD?

---

### Post by geirha on 2008-01-08
> **arunsub said:**
> Geirha & Vanadium, I'll try that. How do I just mount '/' partition without mounting other partitions from the live CD?

If you run the command I posted, it doesn't matter if other filesystems are mounted. The -x option ignores all other filesystems, so it will only show what's actually located on / filesystem. So, if /media displays a lot of used space, it's probably the culprit. You've probably copied some files to one of your other filesystems, only the filesystem you intended to copy to wasn't mounted at the time (I've done that myself a couple of times) so all the files are stored on the / filesystem instead.

When you find a dir that takes up a lot of space, change the du command to check that dir. For example:
```
du --max-depth=1 -xh /media/
```

If any of the directories in /media are taking up space, unmount them with ```
umount /media/thedir
```

Then check /media/thedir/

---

### Post by vanadium on 2008-01-08
Indeed, using the -x option is way better than first unmounting the other partitions. Thanks!

---

### Post by Nonno Bassotto on 2008-01-08
Can't you just use the Baobab tool (disk usage analyzer) to find out what's taking all that space?

---

### Post by arunsub on 2008-01-08
geirha and vanadium, Thank you very much for your help. It's my Maxtor Onetouch4 external hard drive backup files that were written to /media/OneTouch4 since my external hard drive was switched off. I deleted the files from OneTouch4 folder and I got 6.6GB back. 
Nonno, disk usage analyzer did show that directory with the space occupied, but my external drive was ON at that time, so I thought it was referring my external hard drive. I didn't realize it was the local directory.
Again, Thank you everyone for the help!!!

Another question: When I login as user1, my external hard drive is mounted and shows an icon in the desktop. When I use the user switcher and switch to user2, the icon disappears. When I switch back to user1, it still doesn't appear. Any idea how to access the drive irrespective of which user logs in?

---

### Post by vanadium on 2008-01-09
You should probably mark this thread as Solved and post a new problem in a new thread. Anyway, I guess the behaviour you see is consistent. An external drive is automatically mounted with rights for the current user. If you switch users, you cannot see the icon because the drive is in use by, and with rights for, the other user. If you want to mount the drive for the other user, disconnect it first, then connect it when the other account is active.

Otherwise, you would need to mount it as a "fixed" disk, which would involve adding it to /etc/fstab. At that point, the rights are fixed, usually for root, and you would need to manage access through directory ownership and permissions. And the latter requires a unix compatible file system (= no ntfs or fat)

---

### Post by arunsub on 2008-01-09
Thank you.

---

