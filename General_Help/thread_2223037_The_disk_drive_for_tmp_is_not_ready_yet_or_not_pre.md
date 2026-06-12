---
title: "The disk drive for /tmp is not ready yet or not present. Continue to wait, press S to"
date: 2014-05-09
forum: General Help
---

### Post by chris572 on 2014-05-09
Hi,

I recently switched from XP to **ubuntu 12.04 LTS**. It runs on a 8 yr old Acer Travelmate 4220, OS type 32bit, Intel Processor CPU T2300@166 Ghzx2.
Before I never had experiences with Ubuntu, nevertheless the transfer went very smoothly, without any problems, but, as apparently with many others, during booting the following error message appears: **The** **disk drive for /tmp is not ready yet or not present. Continue to wait, press S to skip mounting or M for manual recovery**
Except of waiting, neither of the other options works, so usually after a few seconds the login page appears.
So I skimmed through the forums and tried (with no shell/terminal skills) to solve the bug. None of it worked so far, also because some commands don't seem to work for me (sudo gedit /etc/fstab; ~/.xsession-errors; ...) Or I tried ls -ld /tmp, but couldn't find an error. Same goes for other recommendations.

Does anybody have another easy-to-do solution, which can be implemented by a total rookie?
Thanks!

---

### Post by philinux on 2014-05-09
Try this solution [http://software.techassistbox.com/the-disk-drive-for-tmp-is-not-ready-yet-or-not-present---ubuntu-1204-lts_329190.html](http://software.techassistbox.com/the-disk-drive-for-tmp-is-not-ready-yet-or-not-present---ubuntu-1204-lts_329190.html)

Lots of hits for that though. 
[https://www.google.co.uk/search?client=ubuntu&channel=fs&q=disk+drive+for+/tmp+is+not+ready+yet+or+not+present.+Continue+to+wait,+press+S+to&ie=utf-8&oe=utf-8&gl=uk&gws_rd=cr&ei=FaxsU7n5Fuy70wXZ9oGYCg](https://www.google.co.uk/search?client=ubuntu&channel=fs&q=disk+drive+for+/tmp+is+not+ready+yet+or+not+present.+Continue+to+wait,+press+S+to&ie=utf-8&oe=utf-8&gl=uk&gws_rd=cr&ei=FaxsU7n5Fuy70wXZ9oGYCg)

---

### Post by chris572 on 2014-05-09
Thanks for this, but no chance.
I already tried once 'sudo mv /tmp /tmp_old' ... without any success. Now it tells me: mv: cannot move '/tmp' to '/tmp_old/tmp': Directory is empty

---

### Post by pfeiffep on 2014-05-09
@[COLOR=#000000]chris572, [/COLOR]I had similar symptoms on my old laptop. I installed (using cli) [bleachbit]("http://bleachbit.sourceforge.net/") and run it priot to  shutdown - symptom gone!
using cli   open a terminal (ctrl-alt-t) and type bleachbit ... follow instructions provided.

---

### Post by chris572 on 2014-05-20
Unfortunately it did not work, but thanks for the hint. I tried with Bleachbit which removed quite a lot, and the message indeed disappeared for a few days, but now it's back....

---

### Post by matt_symes on 2014-05-20
Hi

This may not really be an issue if tmp is actually getting mounted.

It may just be due to slow hardware.

Have you checked to see if it`s mounted ?

Open a terminal and type

mount

Post the output back here.

I assume it`s not using tmpfs due to memory constraints. How much memory does the machine have ?

Kind regards

---

### Post by chris572 on 2014-05-20
Thanks. I have more than 100 GB of free space. Here is what appears in the terminal:

/dev/sda1 on / type ext4 (rw)
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
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)

---

### Post by matt_symes on 2014-05-20
Hi

That looks fine and it is using tmpfs.

Can you post the output of

cat /etc/ fstab

I don`t expect to see anything unusual there.

Kind regards

---

### Post by chris572 on 2014-05-23
Sorry for the delay. Here it is:

cat: /etc/: Is a directory
cat: fstab: No such file or directory

---

### Post by chris572 on 2014-05-23
I also tried this which is recommended by many: sudo mv /tmp /tmp_old
but the result is:
mv: cannot move `/tmp' to `/tmp_old/tmp': Directory not empty

---

### Post by Bashing-om on 2014-05-23
chris572; Hi !

Just passing by, but I do notice that your difficulty with Matt's request is a slight slip of the fingers.
Correct the command to be:
```

cat /etc/fstab

```
Remove that 'space' between / and fstab, then the syntax will be correct.

Then we will be able to carry on.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by chris572 on 2014-05-26
Oh dear, sorry and thanks for noticing!
Here it comes with the correct command:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
#UUID=fb4710c9-a32c-47ed-8ae7-d1a0483a5303 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f21f0ec4-9c6e-4e42-bd90-d15ac36840a1 none            swap    sw              0       0

---

### Post by Bashing-om on 2014-05-26
chris572; UnGood !

this
```

#UUID=fb4710c9-a32c-47ed-8ae7-d1a0483a5303 / ext4 errors=remount-ro 0 1

```
with the entry commented out (the '#' character at the start of the line) the entry will not be parsed. Thus the "root file system" can not be mounted.

Let's see what it is going to take to rectify this situation.
Post back - between code tags - the outputs of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

``` and we will see what is and what should be to fix the fstab ( File System TABle) file.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by chris572 on 2014-05-28
Dear,

I am afraid that I added the hashtag a few weeks ago since it was recommended in one post to solve the bug, because the UUID would be flawed. I think I added it after typing: sudo nano /etc/fstab

Here are the results for the comands in the order you posted them:
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00095140

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   232349695   116173824   83  Linux
/dev/sda2       232351742   234440703     1044481    5  Extended
/dev/sda5       232351744   234440703     1044480   82  Linux swap / Solaris

```

```

Model: ATA TOSHIBA MK1234GA (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  119GB  119GB   primary   ext4            boot
 2      119GB   120GB  1070MB  extended
 5      119GB   120GB  1070MB  logical   linux-swap(v1)

```

```

/dev/sda1: UUID="fb4710c9-a32c-47ed-8ae7-d1a0483a5303" TYPE="ext4" 
/dev/sda5: UUID="f21f0ec4-9c6e-4e42-bd90-d15ac36840a1" TYPE="swap"

```

Thanks again!

---

### Post by Bashing-om on 2014-05-28
chris572; Hey;

That confirms the UUID for the root partition is correct.

remove the comment character, save the file and reboot.

What now is the situation ?

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by chris572 on 2014-05-30
Dear Bashing-om,

I tried, but did not work. I removed the # again in front of the UUID after typing this command
```
sudo nano /etc/fstab
```

However I still have the error after 
```
cat /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fb4710c9-a32c-47ed-8ae7-d1a0483a5303 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f21f0ec4-9c6e-4e42-bd90-d15ac36840a1 none            swap    sw              0       0


```

---

### Post by Bashing-om on 2014-05-30
chris572; Well !

Back to square 1, let's try and identify the cause.
Post back the outputs of terminal commands:
```

ls -la /
ls -la /tmp
ls -ld /tmp
mount
df -h
df -i

```

Depending on what we see is weather we try and (re-)create the directory '/tmp'.

[INDENT][INDENT]there is always a causation ->
[INDENT][INDENT][INDENT]find the cause, find the solution
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris572 on 2014-06-03
Dear Bashing-om, after observing all the last few days I can say that the message during booting has disappeared, at least for now.
Instead, now a very brief message appears during shutting down the computer. However, too quick, so I can't read anything. Otherwise all goes normal.
Nevertheless here are the outputs you suggested, maybe sth is still wrong. Thanks again

```
ls -la /
total 100
drwxr-xr-x  24 root root  4096 May 28 22:21 .
drwxr-xr-x  24 root root  4096 May 28 22:21 ..
drwxr-xr-x   2 root root  4096 Apr 11 13:53 bin
drwxr-xr-x   3 root root  4096 May 28 22:21 boot
drwxr-xr-x   2 root root  4096 Apr 11 13:48 cdrom
drwxr-xr-x  16 root root  4120 Jun  3 20:00 dev
drwxr-xr-x 141 root root 12288 Jun  3 20:01 etc
drwxr-xr-x   4 root root  4096 Apr 11 20:31 home
lrwxrwxrwx   1 root root    34 May 28 22:21 initrd.img -> /boot/initrd.img-3.11.0-22-generic
lrwxrwxrwx   1 root root    34 Apr 25 22:18 initrd.img.old -> /boot/initrd.img-3.11.0-20-generic
drwxr-xr-x  20 root root  4096 Apr 11 13:53 lib
drwx------   2 root root 16384 Apr 11 13:42 lost+found
drwxr-xr-x   2 root root  4096 Jun  2 20:46 media
drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt
drwxr-xr-x   3 root root  4096 Apr 27 20:23 opt
dr-xr-xr-x 175 root root     0 Jun  3 19:59 proc
drwx------   7 root root  4096 May 30 16:09 root
drwxr-xr-x  22 root root   780 Jun  3 20:02 run
drwxr-xr-x   2 root root  4096 May 28 22:18 sbin
drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux
drwxr-xr-x   2 root root  4096 Feb  4 12:58 srv
dr-xr-xr-x  13 root root     0 Jun  3 19:59 sys
drwxrwxrwt  12 root root  4096 Jun  3 20:18 tmp
drwxrwxrwt  12 root root  4096 May  5 21:33 tmp_old
drwxr-xr-x  10 root root  4096 Feb  4 12:58 usr
drwxr-xr-x  13 root root  4096 Jun  2 22:31 var
lrwxrwxrwx   1 root root    30 May 28 22:21 vmlinuz -> boot/vmlinuz-3.11.0-22-generic
lrwxrwxrwx   1 root root    30 Apr 25 22:18 vmlinuz.old -> boot/vmlinuz-3.11.0-20-generic
```

```
ls -la /tmp
total 52
drwxrwxrwt 12 root    root    4096 Jun  3 20:29 .
drwxr-xr-x 24 root    root    4096 May 28 22:21 ..
drwxrwxrwt  2 lightdm lightdm 4096 Jun  3 20:00 at-spi2
srw-rw-rw-  1 root    root       0 Jun  3 20:00 cmg-statistic
drwxrwxrwt  2 root    root    4096 Jun  3 20:01 .ICE-unix
drwx------  2 chris   chris   4096 Jun  3 20:01 keyring-3JyOfK
drwx------  2 chris   chris   4096 Jan  1  1970 orbit-chris
drwx------  2 chris   chris   4096 Jun  3 20:15 plugtmp
drwx------  2 lightdm lightdm 4096 Jun  3 20:01 pulse-2L9K88eMlGn7
drwx------  2 root    root    4096 Jun  3 19:59 pulse-PKdhtXMmr18n
drwx------  2 chris   chris   4096 Jun  3 20:01 pulse-yGX0gifnuaoA
srwxrwxr-x  1 chris   chris      0 Jun  3 20:01 qtsingleapp-cav-e7d7-3e8
-rw-rw-r--  1 chris   chris      0 Jun  3 20:01 qtsingleapp-cav-e7d7-3e8-lockfile
drwx------  2 chris   chris   4096 Jun  3 20:01 ssh-wZFBzZwN1751
-rw-rw-r--  1 lightdm lightdm    0 Jun  3 20:00 unity_support_test.0
-r--r--r--  1 root    root      11 Jun  3 20:00 .X0-lock
drwxrwxrwt  2 root    root    4096 Jun  3 20:00 .X11-unix
```

```
ls -ld /tmp
drwxrwxrwt 12 root root 4096 Jun  3 20:29 /tmp
```

```
mount
/dev/sda1 on / type ext4 (rw)
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
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
```

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       109G  5.3G   99G   6% /
udev            492M  4.0K  492M   1% /dev
tmpfs           100M  860K  100M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            500M  224K  500M   1% /run/shm
```

```
df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda1      7266304 271976 6994328    4% /
udev            125762    493  125269    1% /dev
tmpfs           127964    418  127546    1% /run
none            127964      1  127963    1% /run/lock
none            127964      7  127957    1% /run/shm
```

---

### Post by Bashing-om on 2014-06-03
chris572; Hey;

All except 'mount' looks good .. I do not see entries in the mount output I expected to see. -how come, why not -
Let me do a bit of investigations and I will return.

[INDENT][INDENT]inquiring minds
[INDENT][INDENT][INDENT]want to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-06-04
chris572; Hey;

The "how come why not " -> I do not run a standard install and as such the outputs are different.

I did compare your mount output to a standard system's and I see now no problem with your mount output.

Perhaps you were a victim of this bug - fixed in later releases- :
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1091792](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1091792)

If this issue should arise again, might try the proposed solution in that bug report.

If the original query is concluded. please mark this thread solved, and open a new thread on this new issue.

[INDENT][INDENT]we just keep on
[INDENT][INDENT][INDENT]keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

