---
title: "Change owner or something else ?"
date: 2016-08-06
forum: General Help
---

### Post by 4kh3RAm on 2016-08-06
How can I do file copies, edits, etc on my sdb drive without having to use root actions ?

I think I tried changing owner to me, but owner stayed as root.

---

### Post by &amp;KyT$0P# on 2016-08-06
Please open a Terminal in the folder in question and post here the output of
```
ls -la
```

---

### Post by 4kh3RAm on 2016-08-06
Ok.

It looks like you are trying to see who the owner is.


```
total 6718544
drwxr-xr-x 2 root root       4096 Aug  6 21:44 .
drwxr-xr-x 4 root root       4096 Jul 18 19:41 ..
-rwxrwxrwx 1 root root      26032 Mar  4 17:19 3_4_16_Puppy_6.3.0_Bash_Scripts.zip
-rwxrwxrwx 1 root root   59012084 Mar  4 19:37 3_4_16_Puppy_6.3_Documents.zip
-rw-r--r-- 1 root root   23722916 Jul 23 19:03 4kvideodownloader_4.1-1_amd64.deb.zip
-rwxrwxrwx 1 root root   23376910 Feb 16 18:13 4kyoutubetomp3_2.12-1_i386.deb.zip
-rw-r--r-- 1 root root   23433731 Jul 23 19:03 4kyoutubetomp3_3.0-1_amd64.deb.zip
-rw-r--r-- 1 root root      85432 Jun 29 19:16 AARP_HMO_Info.pdf
-rw-r--r-- 1 root root     367565 Aug  1 22:20 Alien_Sunset.jpg.7z
-rwxrwxrwx 1 root root      51710 Apr 13 08:29 aOO-4.1.2_dsktp2.pet.zip
-rwxrwxrwx 1 root root        415 Apr 23 14:30 bashrc.zip
-rwxrwxrwx 1 root root      43353 Aug  6 20:18 bookmarks.html
-rw-r--r-- 1 root root      19625 Jul  8 20:48 bookmarks.zip
-rwxrwxrwx 1 root root      53730 Jun 20 18:03 Brother_2240_Drivers.zip
-rw-r--r-- 1 root root       6757 Jun 30 00:32 candi-1.4.pet.zip
-rw-rw-r-- 1 root root   91036972 Aug  6 21:26 Canon_Movie_8_6_16.MP4.zip
-rwxrwxrwx 1 root root     660333 Jun 20 18:06 Canon_Scanner_Drivers.zip
-rw-r--r-- 1 root root   24368864 Jul 29 20:52 Canon_Vixia_HF_R600_HFR600_Camcorder.zip
-rw-rw-r-- 1 root root        715 Jul 16 07:54 channels.conf.zip
-rw-r--r-- 1 root root  187004564 Jul 13 15:04 clonezilla-live-2.4.7-8-amd64.zip
-rw-r--r-- 1 root root  296014106 Jul 21 17:09 COSTA RICA IN 4K 60fps (ULTRA HD) w  Freefly Movi.mp4.zip
-rwxrwxrwx 1 root root      83022 Mar 20 17:29 CPUtemp-1.9.pet.zip
-rw-r--r-- 1 root root       1120 Aug  6 14:12 cursor.o
-rwxrwxrwx 1 root root     163141 Mar  5 08:34 dcfldd-1.3.4-1.tar.gz
-rwxrwxrwx 1 root root      81350 Apr 16 11:02 ddosim-0.2.tar.gz
-rw-r--r-- 1 root root        901 Jun 30 00:32 debbi-1.2.pet.zip
-rw-r--r-- 1 root root     757562 Jun 15 18:16 efax-gtk_wheezy-3.2.13.pet
-rwxrwxrwx 1 root root     754510 Jun 16 19:30 efax-gtk_wheezy-3.2.13.pet.zip
-rw-r--r-- 1 root root 3780308999 Aug  5 22:00 Family_Movies.zip
-rwxrwxrwx 1 root root    1036934 Apr 24 15:42 Find_Util.zip
-rw-rw-r-- 1 root root       9930 Aug  1 15:24 firework3.zip
-rwxrwxrwx 1 root root     920387 Mar  4 12:48 flburn_0.0.3_i386.deb.zip
-rw-rw-r-- 1 root root       1184 Aug  5 02:22 Franks_NASM_Program.zip
-rw-r--r-- 1 root root        342 Jul  6 17:25 fstab_Puppy_6.3.0.zip
-rwxrwxrwx 1 root root       2517 May 30 10:35 Geany_Conf.zip
-rw-r--r-- 1 root root      18964 Jun 30 00:33 hddtemp-0.3-beta15-52_i386.pet.zip
-rw-r--r-- 1 root root    6042579 Jun 29 14:37 Healthcare_Attachments_2016629.zip
-rwxrwxrwx 1 root root    1159339 Mar 13 04:00 ihex-linux-v095.tar.bz2
-rwxrwxrwx 1 root root     196420 May 17 14:30 Impt_Healthcare_Gov.zip
-rw-rw-r-- 1 root root    2912887 Aug  1 23:22 iview442_x64.zip
-rwxrwxrwx 1 root root       6032 May 30 10:24 jwmrc.zip
-rwxrwxrwx 1 root root     897211 Apr 16 15:20 libnet.zip
-rw-r--r-- 1 root root    5012275 Aug  1 15:51 masm32v11r.zip
-rwxrwxrwx 1 root root   60825086 Apr  8 15:22 Mazda CX7 CX-7 Service Repair Workshop Manual 2007-2012.pdf.zip
-rwxrwxrwx 1 root root    8648638 Apr 25 17:34 mscorefonts.zip
-rw-r--r-- 1 root root     125210 Jun 30 16:12 multi-timer.zip
-rwxrwxrwx 1 root root  492890224 Aug  6 14:36 MUSIC.zip
-rwxrwxrwx 1 root root      73149 May  9 14:47 pburn-4.3.16.pet.zip
-rwxrwxrwx 1 root root     146146 Mar  6 09:58 ppm_auto-2.pet.zip
-rw-r--r-- 1 root root   15588016 Jun 29 18:52 Provider_List.zip
-rw-rw-r-- 1 root root      45210 Jul 15 23:42 Puppy_6.3.0_Bash_Scripts.zip
-rwxr-xr-x 1 root root    2566297 Jul 15 23:32 Puppy_6.3.0_Linux_Icons.zip
-rwxrwxrwx 1 root root      88170 Jun  3 13:04 Puppy_6.3.0_Sound_Effects.zip
-rwxrwxrwx 1 root root        956 May 30 10:33 Puppy_6.3.0_Thunar_Settings.zip
-rwxr-xr-x 1 root root    5521717 Jul  7 17:36 Puppy_6.3_Documents.zip
-rwxrwxrwx 1 root root    6526148 Feb  3  2016 Puppy_6.3_Linux_Documents.zip
-rwxrwxrwx 1 root root   12040184 Jun 19 19:10 python-2.7.5-i486-1.txz
-rwxrwxrwx 1 root root   18964708 Jun 14 13:18 Refill_Repl
```

---

### Post by wildmanne39 on 2016-08-06
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by &amp;KyT$0P# on 2016-08-06
> **4kh3RAm said:**
> It looks like you are trying to see who the owner is.
Among other things, yes.

Two ways to fix it in your case.  You can either make yourself owner
```
sudo chown andy <the folder>
```

or make yourself the group and give the group write permission
```
sudo chgrp andy <the folder>
sudo chmod g+w <the folder>
```


Existing files will still be owned by root, if you want to change that as well, instead use the chown command with added -R flag
```
sudo chown -R andy <the folder>
```

---

### Post by 4kh3RAm on 2016-08-07
Thanks halogen2,

Nice to know that I do not have to tiptoe around a minefield when replying to you. :-)

> sudo chown andy /media/andy/MAXTOR_SDB1/Linux_Files/

Owner was NOT changed.

---

### Post by coffeecat on 2016-08-07
> **4kh3RAm said:**
> 
Owner was NOT changed.

I can see a few possibilities there.

First - what is the filesystem of the sdb drive? Post the output of this terminal command:

```
mount
```

Please enclose the output in code tags, not quote tags, in order to preserve formatting.

Also - how are you mounting the drive? Do you automount from the GUI, or are you using a line in /etc/fstab, or a single line terminal command?

If the filesystem of the sdb drive is a Microsoft one such as NTFS or FAT32, then chown will have no effect - ownership and permissions are defined by the mount options with NTFS or FAT32. If, however, the filesystem of the sdb drive is a Linux one, such as ext3 or ext4, then the command you ran (sudo chown andy /media/andy/MAXTOR_SDB1/Linux_Files/) will only have changed the ownership of the Linux_Files folder, not any files within that folder. So...

**If and only if** the filesystem is a Linux one, have you tried copying a new file to the Linux_Files folder? You should have no trouble with that. Or if you wish to change ownership of all files to andy in the Linux_Files folder, you need to add the recursive option, thus:

```
sudo chown -R andy: /media/andy/MAXTOR_SDB1/Linux_Files/
```

Note also that I have added a trailing colon to your username in that command. The command as you ran it would only change the owner, not the group. The file/folder would still be group owned by root, and you would get an ownership of andy:root, which would be odd. Adding a trailing colon means that the group would be set to your default group. Normally, for you, this would be the andy group, but if you set up a special default group for your own purposes, this trick is a useful one.

**Note:** once again I stress that all those comments about the chown command only apply to Linux filesystems. If you are using a Microsoft filesystem, you need to look elsewhere for the source of the problem, hence the request for the output of the mount command.

---

### Post by mook765 on 2016-08-07
Hi Andy,
the command```
sudo chown andy /media/andy/MAXTOR_SDB1/Linux_Files/
```
will change the ownership off the directory named Linux_Files which i guess, includes the files listed in your post above.
The ownership off the files you want to access will not be changed.
You would have to use the chown-command for every file in your directory, or use wildcards in a single command for all files in the directory.
The ownership is indeed not a problem, if you configure the permissions correctly.
That leads me to the question, which file-system ( NTFS, Ext ) is used on the partition where the files are stored and how do you mount the partition ?

Edit:
@coffecat
sorry, couldn't see your post before i started to write my post.
So there was no intention to repeat the mentioned points.

@ Andi
this ia a nice command as well```
info coreutils 'chown invocation'
```

---

### Post by 4kh3RAm on 2016-08-07
> **coffeecat said:**
> I can see a few possibilities there.

First - what is the filesystem of the sdb drive? Post the output of this terminal command:

```
mount
```

Please enclose the output in code tags, not quote tags, in order to preserve formatting.

Also - how are you mounting the drive? Do you automount from the GUI, or are you using a line in /etc/fstab, or a single line terminal command?

If the filesystem of the sdb drive is a Microsoft one such as NTFS or FAT32, then chown will have no effect - ownership and permissions are defined by the mount options with NTFS or FAT32. If, however, the filesystem of the sdb drive is a Linux one, such as ext3 or ext4, then the command you ran (sudo chown andy /media/andy/MAXTOR_SDB1/Linux_Files/) will only have changed the ownership of the Linux_Files folder, not any files within that folder. So...

**If and only if** the filesystem is a Linux one, have you tried copying a new file to the Linux_Files folder? You should have no trouble with that. Or if you wish to change ownership of all files to andy in the Linux_Files folder, you need to add the recursive option, thus:

```
sudo chown -R andy: /media/andy/MAXTOR_SDB1/Linux_Files/
```

Note also that I have added a trailing colon to your username in that command. The command as you ran it would only change the owner, not the group. The file/folder would still be group owned by root, and you would get an ownership of andy:root, which would be odd. Adding a trailing colon means that the group would be set to your default group. Normally, for you, this would be the andy group, but if you set up a special default group for your own purposes, this trick is a useful one.

**Note:** once again I stress that all those comments about the chown command only apply to Linux filesystems. If you are using a Microsoft filesystem, you need to look elsewhere for the source of the problem, hence the request for the output of the mount command.

```
mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=3523980k,nr_inodes=880995,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=708652k,mode=755)
/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=27,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sdb2 on /media/andy/MAXTOR_SDB2 type ext3 (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdb1 on /media/andy/MAXTOR_SDB1 type ext3 (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdb5 on /media/andy/MAXTOR_SDB5 type ext3 (rw,relatime,errors=remount-ro,data=ordered)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=708652k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)



```

I mount from fstab.

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=a7f207dd-8eb1-4ee5-a06d-bef70bc74536      /                          ext3    errors=remount-ro 0       1
#
UUID=b3b0f384-9e2e-45f5-8995-932f1113f59d      /media/andy/MAXTOR_SDB1    ext3    errors=remount-ro 0       1
#
UUID=fd00f2d7-d666-4614-885d-5ace942dd3f6      /media/andy/MAXTOR_SDB5    ext3    errors=remount-ro 0       1
#
UUID=8adebdf0-6bc3-4eee-8363-3e9440688d42      /media/andy/MAXTOR_SDB2    ext3    errors=remount-ro 0       1

```

I can  copy files there, but I have to do so as a superuser which I would like to avoid.

---

### Post by 4kh3RAm on 2016-08-07
This changed owner to andy,

```
sudo chown -R andy: /media/andy/MAXTOR_SDB1/Linux_Files/

```
But this does not work.

```
cd ~/Documents
zip -u Ubuntu_Documents.zip *.txt *.doc *.rtf *.html *.png *.pdf *.odt *.ods *.odg
cp -u -f Ubuntu_Documents.zip /media/andy/MAXTOR_SDB1/Linux_Files
```

---

### Post by coffeecat on 2016-08-07
@4kh3RAm, your sdb filesystems - there are three partitions - are Linux ones, so you can ignore the comments about NTFS and FAT32. You can chown a Linux filesystem by chown-ing the mountpoint while it is mounted, which has the slightly non-intuitive effect of changing the ownership of the filesystem, and not the mountpoint. Although if you run a "ls -l" command the mountpoint appears to be owned by whoever owns the filesystem.

But enough of details. Let's get this sorted out once and for all for you.

Make sure the three partitions, sdb1, sdb2 and sdb5 are mounted by means of /etc/fstab, and run these three commands exactly as I have written them. Or if you only want to change ownership on one or two partitions, just do the relevant ones.

```
sudo chown andy: /media/andy/MAXTOR_SDB1
sudo chown andy: /media/andy/MAXTOR_SDB2
sudo chown andy: /media/andy/MAXTOR_SDB5
```

Don't forget the trailing colon after your name in each command - if you don't know what that does, re-read my earlier post.

What those commands will do is to make you the owner of the sdb1, sdb2, and sdb5 filesystems, but it will not change the ownership of all the existing files and folders. You will be able to create new folders as yourself, but not save files to folders still owned by root. You now need to do:

```
sudo chown -R andy: /media/andy/MAXTOR_SDB1
sudo chown -R andy: /media/andy/MAXTOR_SDB2
sudo chown -R andy: /media/andy/MAXTOR_SDB5
```

Once you've done that, all files, folders, and the filesystems themselves will be owned by you and you won't need to use sudo. It's quite possible that the second set of commands will achieve what the first does, but I haven't tested this recently, and it won't do any harm to do both sets.

---

### Post by 4kh3RAm on 2016-08-07
Thanks.

I do not know why, but some files are still owned by root instead of andy ?

I do not know if it is because of something I am doing ?

I assume that is why this failed. 

```
zip -u Ubuntu_Documents.zip *.txt *.doc *.rtf *.html *.png *.pdf *.odt *.ods *.odg
        zip warning: name not matched: *.rtf
        zip warning: name not matched: *.ods
zip I/O error: Permission denied
zip error: Could not create output file (Ubuntu_Documents.zip)
```

Both of the files in my Documents folder and the backup folder are owned by root.

---

### Post by 4kh3RAm on 2016-08-07
I think I got it fixed.

For some reason thunar Scripts always opens as root. ??

While thunar Documents does not.

Mystery.

I need another file manager to open my Scripts directory so I can have a shortcut on my desktop and not create root owner files. :-)

---

### Post by coffeecat on 2016-08-07
Where is your Documents folder? Is it in your home folder? If so, this has nothing to do with your problems with the sdb drive, which should all be solved now. If you have root-owned files in a folder within your home folder, then you have all the information you need in this thread to be able to revert the ownership to andy.  It's just a matter of applying the principles explained in this thread and adapting the chown command.

---

### Post by 4kh3RAm on 2016-08-07
Thanks, I went with Rox Filer to display my Scripts directory.

Fixing to make a post about Rox Filer.

---

### Post by mook765 on 2016-08-07
I followed this thread very concentrated and took the opportunity to try a lot of things and to gather more information about the topic.

About NTFS
NTFS doesn't support permissions.
So Linux will emulate them, by default the permissions for the file-system and any files and folders in it will be rwxrwxrwx.
The ownership off the file-system and any file and folders depends on who initiated the mount-process, if it is mounted during start-up (fstab) it will be owned by root, group root.
If it is mounted by the user ( right-click > mount ), the files-ystem and any files and folders will be owned by the user, group user.
It doesn't really matter who the owner is, as everybody has full access to the file-system, a consequence off the permissions.
Warning!!!
For storing data in a private environment that might be ok, in a network it's pretty dangerous...
The advantage is that you don't need to think about permissions or ownership, which might be a difficult chapter...
It's not that i recommend NTFS, i just want to show one more solution for the problem...

---

### Post by 4kh3RAm on 2016-08-07
You make a lot of good points.

I am in a private environment with only one person who has access to my computer.

Windows was too loose with it's administrator mode and elevated privileges with the consequences of getting malware and viruses.

That has never happened since I started using Linux.

---

