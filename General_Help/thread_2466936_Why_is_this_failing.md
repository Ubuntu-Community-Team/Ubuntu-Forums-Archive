---
title: "Why is this failing?"
date: 2021-09-10
forum: General Help
---

### Post by WB0HYQ on 2021-09-10
This is a directory in my home directory that I am trying to delete. Every time I try, I get "Operation not Permitted." Even when I elevate myself to root, I cannot do it.

```

root@bill-UBU:/home/bill# ls -ald Novels
drwxrwxrwx 2 bill bill 4096 Sep  2 21:10 Novels
root@bill-UBU:/home/bill# rmdir Novels
rmdir: failed to remove 'Novels': Operation not permitted
root@bill-UBU:/home/bill#

```

If I move up a directory, I see that somehow I am NOT the owner of my own home directory. Something named "124" is the group and not "bill". Can this be changed?

```

root@bill-UBU:/home# ls -ald bill
drwxrwxrwx+ 110 bill 124 12288 Jul  3 21:25 bill
root@bill-UBU:/home# 

```

Found the 'change group' command. It still does not work.

```

root@bill-UBU:/home# chgrp bill bill
chgrp: changing group of 'bill': Operation not permitted
root@bill-UBU:/home#

```

Really confused, as I thought root could do anything. Any help here? 

Bill

---

### Post by Dennis N on 2021-09-10
```
drwxrwxrwx 2 bill bill 4096 Sep  2 21:10 Novels
root@bill-UBU:/home/bill# rmdir Novels
```

Novels is a directory
**rmdir** will not work unless the directory is empty. Could be file(s) inside?

If you want to remove the directory and its contents, use **rm -r Novels**

---

### Post by WB0HYQ on 2021-09-10
I should have shown the commands prior to trying to remove the directory. I'd emptied it completely. There are no files inside Novels. Wouldn't the error have been "Directory not Empty" if there files in it?

```

bill@bill-UBU:~$ rm -r Novels
rm: cannot remove 'Novels': Operation not permitted
bill@bill-UBU:~$ sudo su
[sudo] password for bill: 
root@bill-UBU:/home/bill# rm -r Novels
rm: cannot remove 'Novels': Operation not permitted
root@bill-UBU:/home/bill#

```

Bill

---

### Post by ActionParsnip on 2021-09-10
Is the folder stored on an NTFS file system by any chance?

---

### Post by WB0HYQ on 2021-09-10
Another oddity:

the commands  compgen -u   and  compgen -g  show no group/user named "124" as shown in my second code block above. Maybe I have a ghost in the machine.

Bill

---

### Post by WB0HYQ on 2021-09-10
> **ActionParsnip said:**
> Is the folder stored on an NTFS file system by any chance?

Not that I know of. The system is dual boot (Windows 7 and Ubumtu/XUbuntu) but everything on the Linux side was created when I installed OS.

I booted into Windows 7 and attached the Linux drive, thinking I might be able to remove the directory from Windows. It failed as well, with virtually the same message: 'can't do this.'

Bill

---

### Post by Impavidus on 2021-09-10
See that + after the permissions? From the manual:```
     Following the file mode bits is a single character that specifies
     whether an alternate access method such as an access control list
     applies to the file.  When the character following the file mode
     bits is a space, there is no alternate access method.  When it is a
     printing character, then there is such a method.

     GNU ‘ls’ uses a ‘.’ character to indicate a file with a security
     context, but no other alternate access method.

     A file with any other combination of alternate access methods is
     marked with a ‘+’ character.
```I guess there's your problem.

---

### Post by WB0HYQ on 2021-09-10
Here's the output of the df command:

```

root@bill-UBU:/home/bill# df -T
Filesystem     Type      1K-blocks      Used  Available Use% Mounted on
udev           devtmpfs    8134492         0    8134492   0% /dev
tmpfs          tmpfs       1639368      1752    1637616   1% /run
/dev/sdb1      ext4      240231392  41523268  186481952  19% /                          <<--- Linux
tmpfs          tmpfs       8196824         0    8196824   0% /dev/shm
tmpfs          tmpfs          5120         4       5116   1% /run/lock
tmpfs          tmpfs       8196824         0    8196824   0% /sys/fs/cgroup
/dev/loop2     squashfs      56832     56832          0 100% /snap/core18/2074
/dev/loop0     squashfs     101760    101760          0 100% /snap/core/11606
/dev/loop3     squashfs      56832     56832          0 100% /snap/core18/2128
/dev/loop1     squashfs     101888    101888          0 100% /snap/core/11420
/dev/loop4     squashfs     166784    166784          0 100% /snap/gnome-3-28-1804/145
/dev/loop5     squashfs     168832    168832          0 100% /snap/gnome-3-28-1804/161
/dev/loop6     squashfs      66688     66688          0 100% /snap/gtk-common-themes/1515
/dev/loop8     squashfs      82432     82432          0 100% /snap/shotcut/451
/dev/loop7     squashfs      86912     86912          0 100% /snap/shotcut/282
tmpfs          tmpfs       1639364        24    1639340   1% /run/user/1000
/dev/sdd1      fuseblk   976074748 317910448  658164300  33% /media/bill/My Book       <<--- external USB
/dev/sdc       fuseblk  1953514580   3700672 1949813908   1% /media/bill/Big_U             <<--- internal SATA
/dev/sda1      fuseblk   976758784 209249184  767509600  22% /media/bill/WIN764              <<--- Windows 7
/dev/sde1      fuseblk   244196001 120239331  123956670  50% /media/bill/WD_PASSPORT   <<--- External USB
root@bill-UBU:/home/bill#

```

Bill

---

### Post by WB0HYQ on 2021-09-10
> **Impavidus said:**
> See that + after the permissions? From the manual:```
     Following the file mode bits is a single character that specifies
     whether an alternate access method such as an access control list applies to the file.  When the character following the file mode bits is a space, there is no alternate access method.  When it is a
     printing character, then there is such a method.  GNU ‘ls’ uses a ‘.’ character to indicate a file with a security context, but no other alternate access method.

     A file with any other combination of alternate access methods is marked with a ‘+’ character.
```I guess there's your problem.

I don't know what "alternate access" means. What other methods of access are there?

Bill

---

### Post by WB0HYQ on 2021-09-10
Even the setfacl command won't work:

```

root@bill-UBU:/home# ls -ald bill
drwxrwxrwx+ 110 bill 124 12288 Jul  3 21:25 bill
root@bill-UBU:/home# setfacl -b bill
setfacl: bill: Operation not permitted
root@bill-UBU:/home# setfacl -R -b bill
setfacl: bill: Operation not permitted
root@bill-UBU:/home#

```

Bill

---

### Post by HermanAB on 2021-09-10
Are you using AppArmor or SELinux?

---

### Post by WB0HYQ on 2021-09-10
Neither one. Not even sure what they are.

Running Ubuntu 20.04LTS with the X-Windows overlay (It boots up as "Xubuntu"). It was an upgrade from 18.04 and originally 14.04. I have a feeling this would all go away if I reinstalled a fresh copy of 20.04 and overwrote the disk. However, I have a LOT of applications, most of which I wrote myself, and hate to have to recreate them.

Bill.

---

### Post by WB0HYQ on 2021-09-11
> **shamsmalik said:**
> What's your main problem?

I am unable to create/rename/delete ANY directories in my /home/bill directory. I need to remove directories that don't have any files in them, and I would also like to create some new ones at that directory level.

Bill

---

### Post by deadflowr on 2021-09-11
See what 
```
getent group | grep 124
```
shows for the group.

What does getfacl show for /home/bill?

Also what is the file system's mount situation,
look at what
```
mount | grep /dev/sdb1
```
shows

---

### Post by WB0HYQ on 2021-09-11
getent group, with a grep for "124", returns nothing. Without the grep, the list shows no entry for "124".


And the mount situation is:

```

bill@bill-UBU:~$ mount | grep /dev/sdb1
/dev/sdb1 on / type ext4 (rw,relatime,errors=remount-ro)
bill@bill-UBU:~$

```

Bill

---

### Post by WB0HYQ on 2021-09-11
I've created a group named x124 with a GID of 124 and put my username (bill) into it. Now the results of the 'getent group' command is:

```

bill@bill-UBU:~$ getent group | grep 124
x124:x:124:bill
bill@bill-UBU:~$ 

```

Does this help me in any way, or has it muddied the waters? I can delete the group if necessary.

Bill

---

### Post by The Cog on 2021-09-11
What does ```
getfacl /
getfacl /home
getfacl /home/bill
``` say?

---

### Post by WB0HYQ on 2021-09-11
Sorry. Was out of the house mowing lawn.

results of those three commands:

```

bill@bill-UBU:~$ getfacl /
getfacl: Removing leading '/' from absolute path names
# file: .
# owner: root
# group: root
user::rwx
group::r-x
other::r-x

bill@bill-UBU:~$ getfacl /home
getfacl: Removing leading '/' from absolute path names
# file: home
# owner: root
# group: root
user::rwx
group::r-x
other::r-x

bill@bill-UBU:~$ getfacl /home/bill
getfacl: Removing leading '/' from absolute path names
# file: home/bill
# owner: bill
# group: x124                   <<<<--------- THIS is what I cannot change!
user::rwx
user:bill:rwx
group::r-x
group:bill:r-x
mask::rwx
other::rwx
default:user::rwx
default:user:bill:rwx
default:group::rwx
default:group:bill:rwx
default:mask::rwx
default:other::rwx

bill@bill-UBU:~$ 

```

Bill

---

### Post by Holger_Gehrke on 2021-09-11
ACLs are probably not the problem since they always correspond to the permission bits (see "man 5 acl", section "CORRESPONDENCE BETWEEN ACL ENTRIES AND FILE PERMISSION BITS"). In general ACLs are used to grant additional permissions to user(s), they can't be used to take permissions away.
One possible reason might be an error in the file system which has led to the fs being remounted read-only. Try booting from a live USB and running fsck on the file system.
Another possibility are attributes, specifically the "immutable"attribute (which does just what the name implies). Use lsattr to see what - if any - attributes are set for the directory and the file in it.

Holger

---

### Post by WB0HYQ on 2021-09-11
A few days ago, I booted into a live DVD and tried just that. I was unable to mount the drive. No matter what I tried, it failed. I tried several methods which I found in various Linux forums, but none worked. I was probably doing it wrong because the error referred to "mount point" being incorrect. I've never mounted a drive/partition manually. They were either plugged-in USB drives or were SATA drives installed internally and picked up on boot by the OS.

I suppose if absolutely necessary, I could unship the drive from one computer, hook it to a SATA to USB dongle, and plug it into another of my Ubuntu machines. I hope this doesn't matter, but the system is dual-boot with Windows 7 on one physical drive, and Ubuntu on a different physical drive.

Bill

---

### Post by WB0HYQ on 2021-09-12
Still working on this problem. I've found it extends far more than simply trying to remove a directory. Each and every command or application that needs to install a temporary directory/file in my home directory will fail with the error of "operation not allowed." Even though the file system is reported as "ext4," 'fsck' says it isn't recognized as such.

I've messed with this long enough. Time to scrub the disk and start over, even though I'll have a massive rebuild of my applications to perform.

Bill

---

### Post by scorp123 on 2021-09-12
Could it be that your **/home** is mounted read-only in that moment?

---

### Post by WB0HYQ on 2021-09-12
I don't think so. If I try to create a file/directory UNDER one of the directories in /home, it works just fine. Example: /home/Novels (the original undeleteable directory) I can create a new directory or file easily. This would indicate it isn't read-only. However, trying to create /home/foo fails with "operation not allowed."

Bill

---

### Post by scorp123 on 2021-09-13
> **WB0HYQ said:**
> I don't think so.

Sorry if this stuff has been asked before.... But could you please give me the output of these commands (in CODE tags please!) :

```
id

mount

ls -al /home

ls -al /home/bill/

cat /etc/passwd

cat /etc/group
```


> **WB0HYQ said:**
> 
However, trying to create /home/foo fails with "operation not allowed."


Weird. Either this location is read-only... or it's some kind of network share that's mounted in into that place?? Something doesn't add up here ...

---

### Post by WB0HYQ on 2021-09-13
id:

```

bill@bill-UBU:~$ id
uid=1000(bill) gid=1000(bill) groups=1000(bill),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),27(sudo),29(audio),30(dip),44(video),46(plugdev),104(fuse),107(scanner),109(lpadmin),112(nopasswdlogin),113(netdev),124,130(powerdev),144(wireshark)
bill@bill-UBU:~$

```

mount:

```

bill@bill-UBU:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,noexec,relatime,size=8134492k,nr_inodes=2033623,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,noexec,relatime,size=1639368k,mode=755)
/dev/sdb1 on / type ext4 (rw,relatime,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup2 on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/bpf type bpf (rw,nosuid,nodev,noexec,relatime,mode=700)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=17641)
debugfs on /sys/kernel/debug type debugfs (rw,nosuid,nodev,noexec,relatime)
mqueue on /dev/mqueue type mqueue (rw,nosuid,nodev,noexec,relatime)
tracefs on /sys/kernel/tracing type tracefs (rw,nosuid,nodev,noexec,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
fusectl on /sys/fs/fuse/connections type fusectl (rw,nosuid,nodev,noexec,relatime)
configfs on /sys/kernel/config type configfs (rw,nosuid,nodev,noexec,relatime)
/var/lib/snapd/snaps/core18_2074.snap on /snap/core18/2074 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_11606.snap on /snap/core/11606 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core18_2128.snap on /snap/core18/2128 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_11420.snap on /snap/core/11420 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-28-1804_145.snap on /snap/gnome-3-28-1804/145 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-28-1804_161.snap on /snap/gnome-3-28-1804/161 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_1515.snap on /snap/gtk-common-themes/1515 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/shotcut_451.snap on /snap/shotcut/451 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/shotcut_282.snap on /snap/shotcut/282 type squashfs (ro,nodev,relatime,x-gdu.hide)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1639364k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/fuse on /run/user/1000/doc type fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdd1 on /media/bill/My Book type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sdc on /media/bill/Big_U type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sda1 on /media/bill/WIN764 type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,uhelper=udisks2)
bill@bill-UBU:~$

```

ls -al /home:

```

bill@bill-UBU:~$ ls -al /home
total 28
drwxr-xr-x    4 root    root     4096 Sep  2 15:48 .
drwxr-xr-x   29 root    root     4096 Aug  5 16:26 ..
drwxrwxrwx+ 110 bill        124 12288 Jul  3 21:25 bill
drwxrwxrwx   15 testing testing  4096 Sep 10 10:30 testing
bill@bill-UBU:~$

```

ls -al /home/bill:

```

bill@bill-UBU:~$ ls -al /home/bill
total 21488
drwxrwxrwx+ 110 bill  124    12288 Jul  3 21:25  .
drwxr-xr-x    4 root root     4096 Sep  2 15:48  ..
drwxrwxrwx    5 bill bill     4096 Sep 24  2014  .adobe
drwxrwxrwx    3 bill bill     4096 Mar  2  2016  .AndroidStudio1.5
-rw-rw-r--    1 bill bill      104 Dec 23  2015  .apport-ignore.xml
drwxrwxrwx    6 bill bill     4096 Aug 30 15:56  .audacity-data
-rw-------    1 bill bill    38557 Sep 12 15:19  .bash_history
-rw-r--r--    1 bill bill      220 Jun  1  2013  .bash_logout
-rw-r--r--    1 bill bill     3495 Mar  8  2016  .bashrc
-rw-r--r--    1 bill bill     3486 Jun  1  2013  .bashrc~
drwxrwxrwx  107 bill bill     4096 Feb 22  2021  .cache
drwxrwxrwx    2 bill bill     4096 Jul 19  2020 'Calibre Library'
drwxrwxrwx    2 bill bill     4096 Nov  1  2014  .clay
drwxrwxrwx   11 bill bill     4096 Jul 19  2020  .codelite
drwxrwxrwx    3 bill bill     4096 Jul 12  2014  .compiz
drwxrwxrwx    3 bill bill     4096 Jun  1  2013  .compiz-1
drwxrwxrwx  100 bill bill     4096 Sep 11 16:55  .config
-rw-rw-r--    1 bill bill      523 Aug  5  2014  .converseen.conf
-rw-rw-r--    1 bill bill   368197 Nov 18  2020  current-cairo.tar.gz
drwxrwxrwx    3 bill bill     4096 Dec 24  2019  Databases
drwxrwxrwx    3 bill bill     4096 Jun  1  2013  .dbus
drwxrwxrwx    4 bill bill     4096 Feb 14  2016  .designer
drwxrwxrwx    2 bill bill     4096 Sep 10 11:11  Desktop
-rw-rw-r--    1 bill bill      226 Aug 26  2014  .devede
drwxrwxrwx    5 bill bill     4096 Sep 11  2014  .dia
-rw-------    1 bill bill      699 Aug 29  2020  Diggers.kmz
-rw-------    1 bill bill      193 Jan 20  2020  .directory
-rw-rw-rw-    1 bill bill       24 Nov 17  2020  .dmrc
drwxrwxrwx   22 bill bill     4096 Mar  9  2021  Documents
drwxrwxrwx    2 bill bill     4096 Jul 19  2020  .dosbox
drwxrwxrwx    9 bill bill    12288 Sep 12 11:11  Downloads
drwxrwxrwx    8 bill bill     4096 Mar 25  2020  .dropbox
drwxrwxrwx    3 bill bill     4096 Mar 25  2020  Dropbox
drwxrwxrwx    3 bill bill     4096 Mar 19  2020  .dropbox-dist
drwxrwxrwx    2 bill bill     4096 Jan 28  2021  Encfs
-rw-r--r--    1 bill bill     8445 Jun  1  2013  examples.desktop
drwxrwxrwx    2 bill bill     4096 Nov  4  2019  .FFdatabase
drwxrwxrwx    2 bill bill     4096 Jul  4 19:25  .filezilla
drwxrwxrwx    2 bill bill    12288 Jul 12  2014  .fontconfig
drwxrwxrwx    3 bill bill     4096 Feb 14  2020  fontconfig
drwxrwxrwx    3 bill bill     4096 Nov 30  2013  .FontForge
drwxrwxrwx    2 bill bill     4096 Jun  2  2013  .fonts
drwxrwxrwx    2 bill bill     4096 Feb  4  2014  .fontypython
drwxrwxrwx    2 bill bill     4096 Sep 29  2014  .FreeFileSync
drwxrwxrwx    2 bill bill     4096 Jul 15  2014  .freerdp
drwxrwxrwx    4 bill bill     4096 Oct 17  2019  Games
-rw-------    1 bill bill    44111 Jan 21  2021  garima-puri_230x230-1.jpg
drwxrwxrwx    6 bill bill     4096 Sep 10 10:50  .gconf
drwxrwxrwx    3 bill bill     4096 Oct 20  2020  .gEDA
drwxrwxrwx    4 bill bill     4096 Jun 28  2013  .gegl-0.0
drwxrwxrwx   22 bill bill     4096 Jul  5  2014  .gimp-2.6
drwxrwxrwx   24 bill bill     4096 Mar 15  2020  .gimp-2.8
-rw-r-----    1 bill bill        0 Jul 16  2020  .gksu.lock
drwxrwxrwx    3 bill bill     4096 Oct 26  2019  .gnome
drwxrwxrwx    5 bill bill     4096 Nov 18  2020  .gnome2
drwxrwxrwx    2 bill bill     4096 Jun  2  2013  .gnome2_private
drwxrwxrwx    3 bill bill     4096 Dec 15  2013  .gnome-commander
drwxrwxrwx    3 bill bill     4096 Dec 21  2019  .gnupg
drwxrwxrwx    2 bill bill     4096 Jul 19  2020  .gnuradio
drwxrwxrwx    2 bill bill     4096 Jul  6 22:36  .googleearth
-rw-------    1 bill bill        0 Nov 12  2013  .goutputstream-1Z8J6W
-rw-------    1 bill bill        0 Jun 11  2013  .goutputstream-3D6OYW
-rw-------    1 bill bill        0 Nov 10  2013  .goutputstream-49B05W
-rw-------    1 bill bill        0 May 31  2014  .goutputstream-5DVGGX
-rw-------    1 bill bill        0 Sep 21  2013  .goutputstream-5X8O3W
-rw-------    1 bill bill        0 Apr  4  2014  .goutputstream-6KG9CX
-rw-------    1 bill bill        0 Jun  2  2013  .goutputstream-724QXW
-rw-------    1 bill bill        0 Jul 30  2013  .goutputstream-7LCC1W
-rw-------    1 bill bill        0 Jul 16  2013  .goutputstream-7PG9ZW
-rw-------    1 bill bill        0 Aug 20  2013  .goutputstream-9ISK2W
-rw-------    1 bill bill        0 Jul 16  2013  .goutputstream-9N07ZW
-rw-------    1 bill bill        0 Jul  4  2014  .goutputstream-9TYGIX
-rw-------    1 bill bill        0 Jan  1  2014  .goutputstream-AJW08W
-rw-------    1 bill bill        0 Jun 11  2014  .goutputstream-B1D6GX
-rw-------    1 bill bill        0 Jun  8  2014  .goutputstream-BBBAHX
-rw-------    1 bill bill        0 Apr  4  2014  .goutputstream-BFNBDX
-rw-------    1 bill bill        0 Jul 24  2013  .goutputstream-DGZW0W
-rw-------    1 bill bill        0 Jun  1  2013  .goutputstream-DVSPXW
-rw-------    1 bill bill        0 Jun  3  2013  .goutputstream-ESN0XW
-rw-------    1 bill bill        0 Feb 22  2014  .goutputstream-F7KKBX
-rw-------    1 bill bill        0 Jan 16  2014  .goutputstream-FGB09W
-rw-------    1 bill bill        0 Jun 28  2013  .goutputstream-FX5CZW
-rw-------    1 bill bill        0 Oct 21  2013  .goutputstream-GFVH5W
-rw-------    1 bill bill        0 Jan 18  2014  .goutputstream-H48T9W
-rw-------    1 bill bill        0 Oct  4  2013  .goutputstream-HR883W
-rw-------    1 bill bill        0 Jun 15  2013  .goutputstream-HUPLYW
-rw-------    1 bill bill        0 Jul  5  2014  .goutputstream-IMHEIX
-rw-------    1 bill bill        0 Jul  7  2014  .goutputstream-IVGMIX
-rw-------    1 bill bill        0 Dec 12  2013  .goutputstream-JMGU7W
-rw-------    1 bill bill        0 Jul  8  2014  .goutputstream-JTNOIX
-rw-------    1 bill bill        0 Dec  1  2013  .goutputstream-JWZA7W
-rw-------    1 bill bill        0 Jul 10  2014  .goutputstream-KCY9HX
-rw-------    1 bill bill        0 Jun  8  2013  .goutputstream-KXCEYW
-rw-------    1 bill bill        0 Jun 23  2013  .goutputstream-L2LDZW
-rw-------    1 bill bill        0 May  1  2014  .goutputstream-LHW7EX
-rw-------    1 bill bill        0 Jun  8  2013  .goutputstream-MKMFYW
-rw-------    1 bill bill        0 May 11  2014  .goutputstream-OHZAGX
-rw-------    1 bill bill        0 Apr  8  2014  .goutputstream-OYP8DX
-rw-------    1 bill bill        0 Jun 18  2014  .goutputstream-PE4NHX
-rw-------    1 bill bill        0 Mar 22  2014  .goutputstream-Q3BTCX
-rw-------    1 bill bill        0 Jun  4  2013  .goutputstream-Q7BNXW
-rw-------    1 bill bill        0 Jul  4  2014  .goutputstream-RH69HX
-rw-------    1 bill bill        0 Oct  4  2013  .goutputstream-RWVD4W
-rw-------    1 bill bill        0 May  2  2014  .goutputstream-S4V8EX
-rw-------    1 bill bill        0 Jun  2  2013  .goutputstream-SA15XW
-rw-------    1 bill bill        0 Sep 16  2013  .goutputstream-SY4Q3W
-rw-------    1 bill bill        0 May 30  2014  .goutputstream-TPIWGX
-rw-------    1 bill bill        0 Jun 27  2013  .goutputstream-TWAHZW
-rw-------    1 bill bill        0 Aug  3  2013  .goutputstream-V3KC1W
-rw-------    1 bill bill        0 May 12  2014  .goutputstream-V6TSFX
-rw-------    1 bill bill        0 Apr 30  2014  .goutputstream-VOX8EX
-rw-------    1 bill bill        0 May 21  2014  .goutputstream-VQL9FX
-rw-------    1 bill bill        0 Feb 22  2014  .goutputstream-WMDRBX
-rw-------    1 bill bill        0 Dec 23  2013  .goutputstream-WZOM8W
-rw-------    1 bill bill        0 Jun 13  2014  .goutputstream-X0QZGX
-rw-------    1 bill bill        0 Jun 27  2013  .goutputstream-XEMGZW
-rw-------    1 bill bill        0 Jun 25  2014  .goutputstream-Y0UMHX
-rw-------    1 bill bill        0 Mar  6  2014  .goutputstream-YSBECX
-rw-------    1 bill bill        0 Apr 26  2014  .goutputstream-ZCAVEX
-rw-------    1 bill bill        0 Jun  8  2013  .goutputstream-ZJ1SYW
drwxrwxrwx    2 bill bill     4096 Apr 22  2016  .gphoto
-rw-rw-rw-    1 bill bill      266 Nov 20  2019  .gr_fftw_wisdom
-rw-rw-rw-    1 bill bill        0 Nov 20  2019  .gr_fftw_wisdom.lock
drwxrwxrwx    2 bill bill     4096 Oct 26  2019  .grsync
drwxrwxrwx    3 bill bill     4096 Nov 19  2015  .gstreamer-0.10
-rw-rw-r--    1 bill bill      172 Jul 12  2014  .gtk-bookmarks
-rw-rw-rw-    1 bill bill     1573 Jul 15  2020  .gtkrc-2.0
-rw-rw-r--    1 bill bill       18 Aug 12  2014  .gtkrc-2.0~
-rw-rw-r--    1 bill bill      565 Oct 21  2014  .gtktermrc
drwxrwxrwx    7 bill bill     4096 Nov 19  2015  .guayadeque
drwxrwxrwx    2 bill bill     4096 Jun  1  2013  .gvfs
-rw-rw-rw-    1 bill bill    24624 Mar 13  2021  hardware.txt
-rw-------    1 bill bill      707 Aug 28  2020 'Higashikushiro Station.kmz'
drwxrwxrwx    2 bill bill     4096 Jun  1  2013  .hplip
-rw-rw-r--    1 bill bill       33 Oct 14  2020  .httrack.ini
-rw-rw-rw-    1 bill bill    65558 Jul 13  2020  .ICEauthority
drwxrwxrwx    2 bill bill     4096 Feb 14  2016  .idlerc
drwxrwxrwx    6 bill bill     4096 Apr 27  2014  .imagej
drwxrwxrwx    3 bill bill     4096 Dec 26  2015  .instead
drwxrwxrwx    4 bill bill     4096 Jul 27  2014  .java
drwxrwxrwx   10 bill bill     4096 Dec 23  2015  .jedit
drwxrwxrwx    2 bill bill     4096 Jun 19  2016  .kabikaboo
drwxrwxrwx    2 bill bill     4096 Nov  1  2014  .kanatest
drwxrwxrwx    3 bill bill     4096 Jun  4  2013  .kde
-rw-rw-r--    1 bill bill      591 Sep  6  2016  .kdrill
-rw-------    1 bill bill      714 Sep 12  2020 'Kushiro Coalmine Co..kmz'
-rw-rw-r--    1 bill bill 19233136 Aug 20  2013  libflashplayer.so
drwxrwxrwx    3 bill bill     4096 Dec 21  2019  .local
drwxrwxrwx    6 bill bill     4096 Jul 12  2014  .luckyBackup
drwxrwxrwx    3 bill bill     4096 Jun  1  2013  .macromedia
drwxrwxrwx    3 bill bill     4096 Feb 16  2016  .matplotlib
drwxrwxrwx    3 bill bill     4096 Jun  1  2013  .mission-control
drwxrwxrwx    2 bill bill     4096 Aug  2  2016  .mozc
drwxrwxrwx    6 bill bill     4096 Nov 20  2017  .mozilla
drwxrwxrwx    2 bill bill     4096 Jun 20  2014  .mplayer
-rw-rw-rw-    1 bill bill   237907 Nov 30  2019 'Multimedia Database.csv'
drwxrwxrwx    2 bill bill     4096 Feb  9  2021  Music
drwxrwxrwx    5 bill bill     4096 May 26 20:41 'My Music'
drwxrwxrwx    5 bill bill     4096 Oct  4  2014  .mypaint
-rw-------    1 bill bill     4898 Sep 16  2020 'My Places.kmz'
-rw-------    1 bill bill       83 Dec 15  2013  .mysql_history
drwxrwxrwx    7 bill bill     4096 Nov 14  2020  .nbi
drwxrwxrwx    3 bill bill     4096 Nov 14  2020  .netbeans
drwxrwxrwx    3 bill bill     4096 Oct  3  2014  .ninja_ide
drwxrwxrwx    2 bill bill     4096 Sep 11 17:52  Novels
drwxrwxrwx    3 bill bill     4096 Jun  1  2013  .nv
-rw-rw-r--    1 bill bill     1849 Jul 19  2020  .nvidia-settings-rc
-rw-rw-r--    1 bill bill        0 Oct  9  2014  .odbc.ini
-rw-r--r--    1 bill bill      281 Feb 18  2021  .pam_environment
-rw-rw-r--    1 bill bill    27383 Oct 16  2019 'Personal Address Book.csv'
-rw-rw-r--    1 bill bill     4179 Mar 12  2020 'Phoenix Train 1.kmz'
drwxrwxrwx   45 bill bill    20480 Apr 28 16:02  Pictures
drwxrwxrwx    3 bill bill     4096 Aug 15  2014  .pki
-rw-r--r--    1 bill bill      675 Jun  1  2013  .profile
drwxrwxrwx   16 bill bill     4096 Nov 14  2020  Programming
drwxrwxrwx    2 bill bill     4096 Apr 29 17:07  .psensor
drwxrwxrwx    3 bill bill     4096 Aug  5 11:42  Public
drwx------    2 bill bill     4096 Oct 18  2014  .pulse
-rw-------    1 bill bill      256 Jun  1  2013  .pulse-cookie
drwxrwxrwx    3 bill bill     4096 Oct 25  2015  .pyrenamer
-rw-------    1 bill bill       79 Feb 16  2016  .python_history
drwxrwxrwx    2 bill bill     4096 Oct 25  2013  .qt
drwxrwxrwx    4 bill bill     4096 Jul  9  2020  .recoll
drwxrwxrwx    2 bill bill     4096 Apr 29 17:04  .remmina
drwxrwxrwx    3 bill bill     4096 Feb 25  2021  .ripoff
-rw-------    1 bill bill     1575 Jul  3  2013  .ripperXrc
drwxr-xr-x    2 bill bill     4096 Jul 25  2014  .rpmdb
drwxrwxrwx    2 bill bill     4096 Oct 18  2020  screenies
drwxrwxrwx    2 bill bill     4096 Jul  9  2020  .searchmonkey
-rw-rw-rw-    1 bill bill       64 Feb 28  2021  .selected_editor
drwxrwxrwx    3 bill bill     4096 Dec 21  2019  .shutter
drwxrwxrwx    2 bill bill     4096 Jan  5  2018  .smb
drwxrwxrwx    6 bill bill     4096 Apr 28 16:23  snap
drwxrwxrwx   12 bill bill     4096 Nov 14  2020 'Software Installs'
drwxrwxrwx    2 bill bill     4096 Dec  7  2019  Sound
drwxrwxrwx    2 bill bill     4096 Jun 20  2014  .spumux
drwxrwxrwx    4 bill bill     4096 Feb 16  2016  .spyder2
drwxrwxrwx    2 bill bill     4096 Oct 16  2014  .ssh
-rw-r--r--    1 bill bill        0 Aug  2  2016  .sudo_as_admin_successful
-rw-rw-rw-    1 bill bill   106016 Jun 26  2020  system_info.html
drwxrwxrwx    4 bill bill     4096 Oct 16  2019  temp
drwxrwxrwx    2 bill bill     4096 Sep 18  2020  Templates
-rw-rw-rw-    1 bill bill      320 Nov  4  2019  .TempQRCodeFile.png
-rw-r--r--    1 bill bill   237568 Dec 23  2019  test.sqlite
drwxrwxrwx    3 bill bill     4096 Mar  9  2020  .thumbnails
-rw-r--r--    1 bill bill    37888 Nov  2  2019  Thumbs.db
drwxrwxrwx    7 bill bill     4096 Nov 27  2019  .thunderbird
-rw-r--r--    1 bill bill     5120 Sep 15  2020  tLogger
drwxr-xr-x   22 bill bill     4096 May 12 14:19 'To and From Windows'
-rw-------    1 bill bill      704 Aug 28  2020 'Tomamu Station.kmz'
-rw-------    1 bill bill      703 Aug 10  2020 'Tsurumi Line.kmz'
-rw-------    1 bill bill      705 Aug 10  2020 'Tsurumi Station.kmz'
drwxrwxrwx   28 bill bill     4096 Jan  6  2020 '_VB Quick Saves'
drwxrwxrwx    3 bill bill     4096 Sep 11  2020  Videos
drwxrwxrwx    2 bill bill     4096 Jul 14 13:19  .vnc
drwxrwxrwx    2 bill bill     4096 Nov  4  2019  WebPhotoExample
drwxrwxrwx    5 bill bill     4096 Oct 14  2020  websites
drwxrwxrwx    5 bill bill     4096 Oct 28  2013  .WhiteIslandSoftware
drwxrwxrwx    5 bill bill     4096 Sep 10 20:11  .wine
-rw-------    1 bill bill      159 Sep 11 13:03  .Xauthority
-rw-rw-r--    1 bill bill      131 Jul 14  2014  .xinputrc
-rw-rw-r--    1 bill bill     9269 Nov 27  2020  .xscreensaver
-rw-rw-r--    1 bill bill     6691 Feb 15  2016  .xscreensaver-getimage.cache
-rw-rw-r--    1 bill bill       34 May 11  2014  .xsession
-rw-rw-r--    1 bill bill       14 May  2  2014  xsession
-rw-rw-r--    1 bill bill       34 May  1  2014  .Xsession
-rw-------    1 bill bill   511231 Sep 13 09:44  .xsession-errors
-rw-------    1 bill bill    78304 Jun 25 11:14  .xsession-errors.old
-rw-rw-rw-    1 bill bill   253467 Dec 29  2020  x.txt
bill@bill-UBU:~$

```

cat /etc/passwd:

```

bill@bill-UBU:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:105::/var/run/dbus:/bin/false
colord:x:103:108:colord colour management daemon,,,:/var/lib/colord:/bin/false
lightdm:x:104:111:Light Display Manager:/var/lib/lightdm:/bin/false
whoopsie:x:105:114::/nonexistent:/bin/false
avahi-autoipd:x:106:117:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:107:118:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
usbmux:x:108:46:usbmux daemon,,,:/home/usbmux:/bin/false
kernoops:x:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:110:119:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:111:122:RealtimeKit,,,:/proc:/bin/false
speech-dispatcher:x:112:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/false
hplip:x:113:7:HPLIP system user,,,:/var/run/hplip:/bin/false
saned:x:114:123::/var/lib/saned:/bin/false
bill:x:1000:1000:Bill,,none,none,:/home/bill:/bin/bash
mysql:x:117:127:MySQL Server,,,:/nonexistent:/bin/false
xrdp:x:118:128::/var/run/xrdp:/bin/false
dnsmasq:x:120:65534:dnsmasq,,,:/var/lib/misc:/bin/false
systemd-timesync:x:121:133:systemd Time Synchronization,,,:/run/systemd:/bin/false
systemd-network:x:122:134:systemd Network Management,,,:/run/systemd/netif:/bin/false
systemd-resolve:x:123:135:systemd Resolver,,,:/run/systemd/resolve:/bin/false
uuidd:x:100:101::/run/uuidd:/bin/false
_apt:x:125:65534::/nonexistent:/bin/false
cups-pk-helper:x:115:109:user for cups-pk-helper service,,,:/home/cups-pk-helper:/usr/sbin/nologin
geoclue:x:119:129::/var/lib/geoclue:/usr/sbin/nologin
gnome-initial-setup:x:126:65534::/run/gnome-initial-setup/:/bin/false
tcpdump:x:124:141::/nonexistent:/usr/sbin/nologin
gdm:x:127:142:Gnome Display Manager:/var/lib/gdm3:/bin/false
systemd-coredump:x:999:999:systemd Core Dumper:/:/usr/sbin/nologin
tss:x:128:143:TPM software stack,,,:/var/lib/tpm:/bin/false
_flatpak:x:129:145:Flatpak system-wide installation helper,,,:/nonexistent:/usr/sbin/nologin
testing:x:1001:1001:testing,,,,:/home/testing:/bin/bash
bill@bill-UBU:~$

```

cat /etc/group:

```

bill@bill-UBU:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:bill,syslog,testing
tty:x:5:syslog
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:bill,testing
fax:x:21:bill,testing
voice:x:22:
cdrom:x:24:bill,testing
floppy:x:25:bill,testing
tape:x:26:bill,testing
sudo:x:27:bill,testing
audio:x:29:pulse,bill,testing
dip:x:30:bill,testing
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:bill,testing
sasl:x:45:
plugdev:x:46:bill,testing
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
crontab:x:102:
syslog:x:103:
fuse:x:104:bill,testing
messagebus:x:105:
bluetooth:x:106:
scanner:x:107:saned,bill,testing
colord:x:108:
lpadmin:x:109:bill,testing
ssl-cert:x:110:
lightdm:x:111:
nopasswdlogin:x:112:
netdev:x:113:bill,testing
whoopsie:x:114:
mlocate:x:115:
ssh:x:116:
avahi-autoipd:x:117:
avahi:x:118:
pulse:x:119:
pulse-access:x:120:
utempter:x:121:
rtkit:x:122:
saned:x:123:
bill:x:1000:
winbindd_priv:x:125:
mysql:x:127:
xrdp:x:128:
powerdev:x:130:bill,testing
systemd-journal:x:132:
systemd-timesync:x:133:
systemd-network:x:134:
systemd-resolve:x:135:
uuidd:x:101:
input:x:137:
rdma:x:126:
geoclue:x:129:
iocard:x:138:
usrp:x:139:
kvm:x:136:
render:x:140:
tcpdump:x:141:
gdm:x:142:
systemd-coredump:x:999:
tss:x:143:
wireshark:x:144:bill
_flatpak:x:145:
testing:x:1001:
bill@bill-UBU:~$

```

Bill

---

### Post by scorp123 on 2021-09-13
Forgot one:

```
cat /etc/fstab
```

I find it very very odd, because this output you gave:

```
bill@bill-UBU:~$ ls -al /home
total 28
drwxr-xr-x    4 root    root     4096 Sep  2 15:48 .
drwxr-xr-x   29 root    root     4096 Aug  5 16:26 ..
drwxrwxrwx**[COLOR="#FF0000"]+[/COLOR]** 110 bill        124 12288 Jul  3 21:25 bill
```

... indicates that there are additional permissions in play here, on top of the standard Unix permissions we can see. Either advanced access control lists or some kind of network share (NFS? SMB?) from somewhere somehow.

I know that in a previous post you guys already checked for access control lists .... so it's got to be something else.

I also find the liberal permissions of "777" on many of your files ***extremely extremely disturbing*** and weird for a Linux OS. Also the file names themselves are truly bizarre (e.g. Thumbs.db, "My Places", "My Music" ...). If I didn't know it any better I would assume I am looking at a Windows user's home directory that's being mounted in via SMB.

This does not look at all like a native Linux home directory.

Are you perfectly sure there's no network share in play here??

---

### Post by WB0HYQ on 2021-09-13
I copied and pasted a number of standard Windows directories into my home directory ages ago. Since I rarely boot into Windows any more, this was the best way (at the time) to view the contents. I did this long ago, back when my version of Ubuntu was 14.04.6. I never had any troubles until I upgraded from 18.04 to 20.04, then the fun started. I know full well that each in-place OS upgrade can throw all kinds of monkey wrenches into the gears. I feel that this is what happened. My only question is: why did it happen six months after upgrading to 20.04? I would have expected it to happen immediately.

To try and straighten out all the permissions and such would be a giant pain, so I am about convinced to clean the entire HDD and start over.

You mentioned Samba (SMB). I seem to remember a while back using Samba sharing was the only way I could "see" my Linux system from the other computers (all Windows then) on my LAN. I have seven of them and most are converted to Linux now. This is probably an artifact of that sharing. That "124" is unchangeable. Trying to alter it was the reason for this whole thread. After your clues, I strongly suspect the "124" is a remnant of a SMB share. HOWEVER, I would not have shared my home directory so openly on my LAN, even though it is a private LAN and behind an impressively well-guarded connection to the Internet through AT&T.

According to Synaptic Package Manager, Samba only shows up under "All" and "Not Installed," so it isn't currently on my system. The dregs remaining from an install could have been left behind. I don't remember uninstalling it. if I did, it was several years ago.

Bill

---

### Post by TheFu on 2021-09-13
```
sudo chown -R bill:bill /home/bill

# as "bill" userid
rmdir /home/bill/Novels
```

If that doesn't work, then
[LIST=1]
[*]the parent directory for /home/bill/Novels isn't owned by bill
[*]/home/bill/Novels isn't really empty
[*]some file system issue, run fsck
[*]some extra ACLs or overwriting the normal permissions for /home/bill/Novels, use **setfacl -bn /home/bill/Novels**
[/LIST]
Use getfacl /home/bill/Novels to see all the ACLs are gone.  Then start at the top again.  You can also disable all ACLs during mount time with the noacl option.  I know that option used to exist, but on a 20.04 system, I cannot find it in the mount manpages (sections 2 or 8)

---

### Post by WB0HYQ on 2021-09-13
Same results as before:

```

bill@bill-UBU:~$ sudo chown -R bill:bill /home/bill
[sudo] password for bill: 
chown: changing ownership of '/home/bill/.local/share/recently-used.xbel': Operation not permitted
chown: changing ownership of '/home/bill': Operation not permitted
bill@bill-UBU:~$ rmdir /home/bill/Novels
rmdir: failed to remove '/home/bill/Novels': Operation not permitted
bill@bill-UBU:~$

```


(1) Already knew this
(2)  /Novels is completely empty. There are no hidden files in it or anything else.
(3) I answered an emphatic "N" to this warning:

```

bill@bill-UBU:~$ fsck
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/sdb1 is mounted.



WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.


Do you really want to continue<n>? 


```

(4) Something changed with the following commands:

```

bill@bill-UBU:~$ setfacl -bn /home/bill/Novels
bill@bill-UBU:~$ getfacl /home/bill/Novels
getfacl: Removing leading '/' from absolute path names
# file: home/bill/Novels
# owner: bill
# group: bill                       <<<------ ! ! ! !
user::rwx
group::rwx
other::rwx

bill@bill-UBU:~$

```

I'm going to log out and do a reboot to see if this now allows me to delete the directory. Back in a few minutes.....

Bill

---

### Post by WB0HYQ on 2021-09-13
No good. Same problem as before. Using a terminal gives the same error as before



[IMG]http://intellisigsys.net/pics/1.png[/IMG]
Bill

---

### Post by TheFu on 2021-09-13
```
chown: changing ownership of '/home/bill': Operation not permitted
rmdir: failed to remove '/home/bill/Novels': Operation not permitted
chown: changing ownership of '/home/bill/.local/share/recently-used.xbel': Operation not permitted
```
!!!!!
Check the file attribs.  **lsattr  /home/bill** is the command.  Could be set to be "immutable".   Can remove that attrib using **chattr** command.

Stay away from the GUI.

If that isn't it, then boot off into a "try ubuntu" environment, mount the storage and try removing it that way.  If that fails, run fsck on the !!!!!UNMOUNTED!!!!  partition and try again.  Never, ever, attempt to run fsck on a currently used/mounted partition/file system. Nothing good can happen.

Which file system is on the?  Could it be btrfs or zfs or something else that isn't normally seen here?

---

### Post by WB0HYQ on 2021-09-13
Okay. Results of the lsattr command:

```

bill@bill-UBU:~$ lsattr /home/bill
--------------e----- /home/bill/snap
--------------e----- /home/bill/Diggers.kmz
--------------e----- /home/bill/x.txt
-----------I--e----- /home/bill/Pictures
--------------e----- /home/bill/_VB Quick Saves
--------------e----- /home/bill/Multimedia Database.csv
--------------e----- /home/bill/Tomamu Station.kmz
--------------e----- /home/bill/Public
--------------e----- /home/bill/Personal Address Book.csv
--------------e----- /home/bill/Programming
-----------I--e----- /home/bill/Downloads
--------------e----- /home/bill/My Music
--------------e----- /home/bill/Thumbs.db
--------------e----- /home/bill/Higashikushiro Station.kmz
--------------e----- /home/bill/Templates
--------------e----- /home/bill/Novels
--------------e----- /home/bill/Dropbox
--------------e----- /home/bill/Music
--------------e----- /home/bill/test.sqlite
--------------e----- /home/bill/Software Installs
--------------e----- /home/bill/Desktop
--------------e----- /home/bill/hardware.txt
--------------e----- /home/bill/Sound
--------------e----- /home/bill/system_info.html
--------------e----- /home/bill/Tsurumi Line.kmz
--------------e----- /home/bill/Calibre Library
--------------e----- /home/bill/websites
--------------e----- /home/bill/Databases
--------------e----- /home/bill/fontconfig
--------------e----- /home/bill/Encfs
--------------e----- /home/bill/WebPhotoExample
--------------e----- /home/bill/screenies
--------------e----- /home/bill/xsession
--------------e----- /home/bill/current-cairo.tar.gz
--------------e----- /home/bill/Games
--------------e----- /home/bill/temp
--------------e----- /home/bill/My Places.kmz
--------------e----- /home/bill/libflashplayer.so
--------------e----- /home/bill/To and From Windows
--------------e----- /home/bill/Tsurumi Station.kmz
--------------e----- /home/bill/Kushiro Coalmine Co..kmz
--------------e----- /home/bill/examples.desktop
--------------e----- /home/bill/Documents
--------------e----- /home/bill/Phoenix Train 1.kmz
--------------e----- /home/bill/Videos
--------------e----- /home/bill/tLogger
--------------e----- /home/bill/garima-puri_230x230-1.jpg
bill@bill-UBU:~$

```

I tried a 'try ubuntu' disk. I couldn't get the drive to mount. Kept giving me errors like 'bad mount point' and stuff like that. I am not very good tinkering with the OS yet.

The file system for /dev/sdb1 is ext4

bill

---

### Post by dragonfly41 on 2021-09-13
This is a very long shot .. although the error message is not "permissions"
As a test, I created a directory named Novels
within $HOME/
and in $HOME I got this ..
[FONT=monospace][COLOR=#000000]$ rmdir Novels[/COLOR]
rmdir: failed to remove 'Novels': No such file or directory

The reason? I had included a space after $HOME/Novels   << space at end.

..

Can you rename the folder?

[/FONT]

---

### Post by WB0HYQ on 2021-09-13
Nope. the 'mv' command says the operation is not permitted. And, in the GUI shot above, the "Rename" is greyed out. An oddity is I can COPY the directory anywhere I want, and do whatever I want to it.

Bill

---

### Post by TheFu on 2021-09-13
> **WB0HYQ said:**
> Nope. the 'mv' command says the operation is not permitted. And, in the GUI shot above, the "Rename" is greyed out. An oddity is I can COPY the directory anywhere I want, and do whatever I want to it.

Bill

copy is read.
mv is write.

Something is preventing write.  There are just a few things that can do that.  I've gone through all of them, but not the corrupted file system. Did an fsck ever get run, then mount the file system under the Try Ubuntu environment and delete it?

[LIST=1]
[*]permissions on the file
[*]permissions on the parent directory
[*]ACLs
[*]attrs
[*]file system corruption
[/LIST]

Those are the possibilities. Ain't nuthin' else.

---

### Post by WB0HYQ on 2021-09-13
I've about had it for today, my friend. Tomorrow, I will boot into the DVD and try a fsck run on the drive. Once before using a Try Ubuntu DVD, I tried to delete the directory and was told the same thing as before.

I think what I have here is a totally messed up file system that has come through many upgrades and shares. Heck, I even tried booting into Windows7 and attaching the Ubuntu drive to delete the directory. No go. Windows only gave me a meaningless error message having to do with "can't read the drive," which was obviously wrong because I could scan through the whole thing, reading and writing files wherever I wanted -- except /home/bill, and the various files/directories in that single directory.

Be back tomorrow.

Bill

---

### Post by WB0HYQ on 2021-09-13
One final gasp before I go....

booted into My Ubuntu DVD. Here are the results of the commands issued:

```

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# fsck /dev/sdb1
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/sdb1: clean, 506230/15269888 files, 11387345/61048952 blocks
root@ubuntu:/home/ubuntu#

```

and using Terminal in Ubuntu Live session) I shifted to the proper /home/bill directory:

```

ubuntu@ubuntu:/media/ubuntu/7120ab16-c27b-414f-93ee-5a636acc41c9/home/bill$ rmdir Novels
rmdir: failed to remove 'Novels': Operation not permitted
ubuntu@ubuntu:/media/ubuntu/7120ab16-c27b-414f-93ee-5a636acc41c9/home/bill$ sudo su
root@ubuntu:/media/ubuntu/7120ab16-c27b-414f-93ee-5a636acc41c9/home/bill# rmdir Novels
rmdir: failed to remove 'Novels': Operation not permitted
root@ubuntu:/media/ubuntu/7120ab16-c27b-414f-93ee-5a636acc41c9/home/bill#

```

Note the above was run as a "user" then again as "root". Still cannot delete that dang directory (or any of the others either).

Now, I'm off to bed.

Bill

---

### Post by TheFu on 2021-09-14
You let Windows access EXT4 partitions!!!!!  Ouch!

---

### Post by WB0HYQ on 2021-09-14
Why is this a problem? Isn't that what "Network Sharing" is all about? Using "Files" I set up the share in Ubuntu and on my various Windows machines, I found it. Most of my shares were on the other drives, which are formatted NTFS. These are either internal or USB connected and were there when my Ubuntu machine was a simple Windows 7 box. When running it in Windows, I CANNOT "see" the Ubuntu drive at all, so I did not let Windows access it. Only through my other machines do I access this computers shared Ubuntu directories AND only when it is running Ubuntu, not Windows.

Makes no difference now as I have reinstalled 20.04LTS from a DVD, reformatting the entire drive first.

According to my old notebooks, I am pretty sure I know where I shot myself in the foot (Ready! Fire! Aim!). I wrote down the instructions for sharing but didn't take into account I was sharing a directory (such as Novels) which was under /home/bill. NOW, I understand this is not a good idea. I plan on moving all the ones I want to share to the NTFS drives and not share a single one from the ext4 drive. I have a lot of shared directories as I am an author. As you can imagine, this created tons of directories and files. I need to be able to access them from other computers, most of which are laptops I take with me on trips.

Anyway, this is how it stand right now. My thanks for everyone's help. Trying to remember what I did years ago is a trial. I am wiser now.

Bill

---

### Post by WB0HYQ on 2021-09-14
Mission accomplished. The re-installation went well and I can now do whatever I want in /home/bill.

My thanks to everyone involved for not only jogging my memory, but helping me with commands to find these errors. Every one of them is now written in my "things to know about Linux that you can't find easily" notebook. THis only proves you can learn something new every day - even at my age (79).

Bill

---

### Post by TheFu on 2021-09-14
CIFS sharing is vastly different today than it was 2 yrs ago.  Beware using old instructions. Mircosoft changed many things to improve win10 security.

Don't know if I've said this enough, but sharing storage from inside any user's HOME is asking for problems.
Sharing storage that isn't native Linux over the network is also asking for problems.
Sharing storing using the GUI to set it up is asking for problems too.  Stick with NFS for Unix-based OSes. Only use CIFS when absolutely necessary and only configure the shares through text configuration files - using either ZFS or Samba.

Be we all have to learn these things on our own, I suppose.  *Easy* trumps *wise* all the time.

---

### Post by WB0HYQ on 2021-09-14
I always was aware of sharing, even before I began experimenting with Linux. I'm currently investigating the installation of a network accessible drive. This way, I won't have to set anything up except for the necessary linkage between whatever computer I am on and the device.

I will never again share anything in the HOME directory.

Thanks for hanging around, Fu.

Bill

---

