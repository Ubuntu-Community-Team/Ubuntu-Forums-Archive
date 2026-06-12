---
title: "mount accessible, but not showing in df"
date: 2020-08-07
forum: General Help
---

### Post by gebseng on 2020-08-07
On my Ubuntu Server 20.04 machine, I have a partition /dev/sda1. In /etc/fstab, it is mounted at /media/gs_archive_05_copy. This worked fine so far.

But now, if I do a df, sda seems to not show up at all:
```
[COLOR=#000000][FONT=Menlo]Filesystem      1K-blocks       Used  Available Use% Mounted on[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]udev              1914956          0    1914956   0% /dev[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]tmpfs              391772      41152     350620  11% /run[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sdb2      3844123664 3844107280          0 100% /[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]tmpfs             1958844          0    1958844   0% /dev/shm[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]tmpfs                5120          0       5120   0% /run/lock[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]tmpfs             1958844          0    1958844   0% /sys/fs/cgroup[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop0           9344       9344          0 100% /snap/canonical-livepatch/95[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop1          98944      98944          0 100% /snap/core/9436[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop2          99328      99328          0 100% /snap/core/9665[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sdc2      1310275740 1140936804  102710768  92% /media/temp[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sdc1      1571899904  449610024 1042372008  31% /media/time_machine[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop3          56320      56320          0 100% /snap/core18/1880[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop4          73088      73088          0 100% /snap/lxd/16099[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sdb1          523248       7944     515304   2% /boot/efi[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop6          73088      73088          0 100% /snap/lxd/16558[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]tmpfs              391768          0     391768   0% /run/user/1000[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop7          56704      56704          0 100% /snap/core18/1885[/FONT][/COLOR]

```

The funny thing is, if I go to  /media/gs_archive_05_copy/ , I can still access the disk's content, so it seems to be mounted. What could be the reason?

---

### Post by gebseng on 2020-08-07
Update on the situation: for some reason,[COLOR=#000000] /media/gs_archive_05_copy[/COLOR] seems to be at /dev sdb2 now.

When I do [COLOR=#000000][FONT=Menlo]df /media/gs_archive_05_copy/, I get this:
[/FONT][/COLOR]```
[COLOR=#000000][FONT=Menlo]Filesystem      1K-blocks       Used Available Use% Mounted on
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]/dev/sdb2      3844123664 3844107280         0 100% /[/FONT][/COLOR]
```[COLOR=#000000][FONT=Menlo]

The disk seems to be full, even though I already deleted several directories. Maybe that's part of the problem?[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]

---

### Post by kneutron on 2020-08-07
--Yeeeeaah, it's not really mounted and you filled up your root filesystem at that mount point. If you delete files there and they're not backed up, they're gone.

---

### Post by gebseng on 2020-08-07
Deleting files is no problem for me. Why did deleting some directories not free up some space, as expected?

---

### Post by kneutron on 2020-08-07
--You might need to fsck root " / ", you can do this with a touch+reboot:

REF: [https://linuxconfig.org/how-to-force-fsck-to-check-filesystem-after-system-reboot-on-linux#:~:text=The%20simplest%20way%20to%20force,in%20the%20partition's%20root%20directory.&text=This%20empty%20file%20will%20temporarily,on%20the%20next%20system%20reboot]("https://linuxconfig.org/how-to-force-fsck-to-check-filesystem-after-system-reboot-on-linux#:~:text=The%20simplest%20way%20to%20force,in%20the%20partition's%20root%20directory.&text=This%20empty%20file%20will%20temporarily,on%20the%20next%20system%20reboot.")

--In future, make sure the drive is mounted first by checking df, you can also ' touch /mnt/point/NOTHERE ' when nothing is mounted there, and the presence of the NOTHERE file will let you know what the deal is when you access the directory. NOTE If something mounts over the top of it, the NOTHERE file will disappear until it's unmounted again.

bash for this:

```

function failexit () {
  echo '! Something failed! Code: '"$1 $2" # code # (and optional description)
  exit $1
}

bkpdest=[COLOR=#000000]/media/gs_archive_05_copy[/COLOR]

[ -e "$bkpdest/NOTHERE" ] && failexit 99 "$bkpdest NOTHERE -- NOT MOUNTED"
# "If" checking for NOTHERE file...


chkmount=$(df |grep -c $bkpdest)
[ $chkmount -gt 0 ] || failexit 99 "$bkpdest NOT MOUNTED"

# If fallthru to here, it's mounted, safe to proceed

```

---

### Post by gebseng on 2020-08-08
Thanks for your advice! Turns out, I had formatted sda1 a week ago, and its UUID had changed. That's why it was not mounted in fstab anymore, and rsync copied everything to root.

---

### Post by kneutron on 2020-08-08
--Did you get the free space back?

---

### Post by gebseng on 2020-08-08
Yes, after deleting some more the free space started showing again

---

