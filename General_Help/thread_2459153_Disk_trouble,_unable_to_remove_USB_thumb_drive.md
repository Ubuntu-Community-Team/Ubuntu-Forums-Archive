---
title: "Disk trouble, unable to remove USB thumb drive"
date: 2021-03-11
forum: General Help
---

### Post by BudworthTDog on 2021-03-11
Okay, so after roughly 12 years of being a strict Linux household for personal computers I have broken down and accepted that I need one Windows computer in house. Blue Iris if you must know. I'm not happy about it but it is what it is.

Anyway that brings me to my issue. I was trying to make a USB Windows bootable disk when it got stuck at 4.2GB. After it hung there for a while I accepted that it was just not working and canceled it. It hung up some more and I eventually just unplugged the USB drive. Now the usb drive is showing up under my devices menu in caja as if its plugged in but not mounted. If I select it an error comes up saying unable to mount an operation is already pending. I tried rebooting (which took longer than usual) and it booted up with the same issue. I tried launching the Disks program but it wont launch. It just does nothing and then after a couple minutes an error pops up saying if couldn't be launched or something. 

This is what I get for trying to install Windows. 

So, any ideas how I can get my linux computer back up and running? I'm not worried about the Windows bootable disk at this point. It's been handled with my work laptop.

---

### Post by Bashing-om on 2021-03-11
BudworthTDog; Hello -

If we can identify the device name that holds that file handler open maybe we can "kill"
the process from what "fuser" tells us, for the relevant PID.

Get any joy to identify the device from terminal command:
```

sudo fdisk -lu

```

[INDENT]got to be a way
[/INDENT]

---

### Post by BudworthTDog on 2021-03-11
I ran that command and nowhere in the output does it list the USB drive that's giving me issues. Looked over it 3 times and nowhere can I find it. its a 64GB USB drive and everything listed (aside from stuff starting with dev/loop) are all 447GB or above. Not only that but it appears as if that complete command can't run. It starts to run but eventually just hags and gives me a blinking curser. I have to close out of the terminal to be able to even put in another command. 

Any other ideas?

---

### Post by Bashing-om on 2021-03-11
BudworthTDog; Ouch

How about
```

sudo blkid -c /dev/null -o list

```

-got to be a way-

---

### Post by BudworthTDog on 2021-03-11
That's even worse somehow lol. This is that I get 

[IMG]https://i.imgur.com/ZPYKPcu.png[/IMG]

---

### Post by Bashing-om on 2021-03-11
BudworthTDog; Yukkie Poo :(

I strething my imigination now but ?
```

lsusb

```

as it is a USB device we seek to know.

-sometimes I do wonder-

---

### Post by BudworthTDog on 2021-03-12
Same result with the lsusb

I just get a blinking curser

---

### Post by Bashing-om on 2021-03-12
BudworthTDog - Sorry

This is now above my skill set to find that file descriptor.
Let's see if others with greater skill come to our aid.

I will remain interested - too for my learning curve.

-Still, there has to be a way-

---

### Post by ajgreeny on 2021-03-12
What does the command ***mount*** show you, followed by ***cat /etc/mtab***.

No promises but it may help or even show us the mount point where that disk was mounted even if it's no longer there; perhaps the mount point folder has got stuck for some reason.

---

### Post by BudworthTDog on 2021-03-12
The mount command gives me the following 

sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,noexec,relatime,size=16355340k,nr_inodes=4088835,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,noexec,relatime,size=3286344k,mode=755)
/dev/sdc2 on / type ext4 (rw,relatime,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup2 on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/bpf type bpf (rw,nosuid,nodev,noexec,relatime,mode=700)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
systemd-1  on /proc/sys/fs/binfmt_misc type autofs  (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=22074)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
mqueue on /dev/mqueue type mqueue (rw,nosuid,nodev,noexec,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,nosuid,nodev,noexec,relatime)
tracefs on /sys/kernel/tracing type tracefs (rw,nosuid,nodev,noexec,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,nosuid,nodev,noexec,relatime)
configfs on /sys/kernel/config type configfs (rw,nosuid,nodev,noexec,relatime)
/var/lib/snapd/snaps/core18_1944.snap on /snap/core18/1944 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core18_1988.snap on /snap/core18/1988 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/snapd_11036.snap on /snap/snapd/11036 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/software-boutique_54.snap on /snap/software-boutique/54 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/sdc1  on /boot/efi type vfat  (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=3286340k,mode=700,uid=1000,gid=1000)
/dev/sdd1 on /media/mrmilo/TV type ext4 (rw,nosuid,nodev,relatime,uhelper=udisks2)
/dev/sde on /media/mrmilo/Movies.and.More type ext4 (rw,nosuid,nodev,relatime,uhelper=udisks2)
/dev/sdb1 on /media/mrmilo/TV Backup type ext4 (rw,nosuid,nodev,relatime,uhelper=udisks2)
/var/lib/snapd/snaps/ubuntu-mate-welcome_592.snap on /snap/ubuntu-mate-welcome/592 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/snapd_11107.snap on /snap/snapd/11107 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/ubuntu-mate-welcome_599.snap on /snap/ubuntu-mate-welcome/599 type squashfs (ro,nodev,relatime,x-gdu.hide)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)


cat /etc/mtab gives me the following 

sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,nosuid,noexec,relatime,size=16355340k,nr_inodes=4088835,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,nodev,noexec,relatime,size=3286344k,mode=755 0 0
/dev/sdc2 / ext4 rw,relatime,errors=remount-ro 0 0
securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
tmpfs /sys/fs/cgroup tmpfs ro,nosuid,nodev,noexec,mode=755 0 0
cgroup2 /sys/fs/cgroup/unified cgroup2 rw,nosuid,nodev,noexec,relatime,nsdelegate 0 0
cgroup /sys/fs/cgroup/systemd cgroup rw,nosuid,nodev,noexec,relatime,xattr,name=systemd 0 0
pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0
efivarfs /sys/firmware/efi/efivars efivarfs rw,nosuid,nodev,noexec,relatime 0 0
none /sys/fs/bpf bpf rw,nosuid,nodev,noexec,relatime,mode=700 0 0
cgroup /sys/fs/cgroup/cpu,cpuacct cgroup rw,nosuid,nodev,noexec,relatime,cpu,cpuacct 0 0
cgroup /sys/fs/cgroup/devices cgroup rw,nosuid,nodev,noexec,relatime,devices 0 0
cgroup /sys/fs/cgroup/hugetlb cgroup rw,nosuid,nodev,noexec,relatime,hugetlb 0 0
cgroup /sys/fs/cgroup/memory cgroup rw,nosuid,nodev,noexec,relatime,memory 0 0
cgroup /sys/fs/cgroup/blkio cgroup rw,nosuid,nodev,noexec,relatime,blkio 0 0
cgroup /sys/fs/cgroup/rdma cgroup rw,nosuid,nodev,noexec,relatime,rdma 0 0
cgroup /sys/fs/cgroup/net_cls,net_prio cgroup rw,nosuid,nodev,noexec,relatime,net_cls,net_prio 0 0
cgroup /sys/fs/cgroup/cpuset cgroup rw,nosuid,nodev,noexec,relatime,cpuset 0 0
cgroup /sys/fs/cgroup/perf_event cgroup rw,nosuid,nodev,noexec,relatime,perf_event 0 0
cgroup /sys/fs/cgroup/pids cgroup rw,nosuid,nodev,noexec,relatime,pids 0 0
cgroup /sys/fs/cgroup/freezer cgroup rw,nosuid,nodev,noexec,relatime,freezer 0 0
systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=22074 0 0
hugetlbfs /dev/hugepages hugetlbfs rw,relatime,pagesize=2M 0 0
mqueue /dev/mqueue mqueue rw,nosuid,nodev,noexec,relatime 0 0
debugfs /sys/kernel/debug debugfs rw,nosuid,nodev,noexec,relatime 0 0
tracefs /sys/kernel/tracing tracefs rw,nosuid,nodev,noexec,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,nosuid,nodev,noexec,relatime 0 0
configfs /sys/kernel/config configfs rw,nosuid,nodev,noexec,relatime 0 0
/dev/loop0 /snap/core18/1944 squashfs ro,nodev,relatime 0 0
/dev/loop1 /snap/core18/1988 squashfs ro,nodev,relatime 0 0
/dev/loop2 /snap/snapd/11036 squashfs ro,nodev,relatime 0 0
/dev/loop3 /snap/software-boutique/54 squashfs ro,nodev,relatime 0 0
/dev/sdc1  /boot/efi vfat  rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro  0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
tmpfs /run/user/1000 tmpfs rw,nosuid,nodev,relatime,size=3286340k,mode=700,uid=1000,gid=1000 0 0
/dev/sdd1 /media/mrmilo/TV ext4 rw,nosuid,nodev,relatime 0 0
/dev/sde /media/mrmilo/Movies.and.More ext4 rw,nosuid,nodev,relatime 0 0
/dev/sdb1 /media/mrmilo/TV\040Backup ext4 rw,nosuid,nodev,relatime 0 0
/dev/loop7 /snap/ubuntu-mate-welcome/592 squashfs ro,nodev,relatime 0 0
/dev/loop6 /snap/snapd/11107 squashfs ro,nodev,relatime 0 0
/dev/loop5 /snap/ubuntu-mate-welcome/599 squashfs ro,nodev,relatime 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0


Not  sure what to make out of all that. The only thing I recognize is the  TV, TV Backup and, Movies and More disks me mounted, which they are
****

---

### Post by ajgreeny on 2021-03-13
Not much help I'm  afraid.

Try booting again but removing quiet splash from the boot default by hitting E at grub menu to edit the line just the one time.
If we're  lucky there may be some message shown in the text boot while the system tries to do something with that errant disk.

---

### Post by BudworthTDog on 2021-03-14
Well it seems to have fixed itself. After another reboot the problem went away. Thanks all for your help.

---

### Post by ajgreeny on 2021-03-14
Great news! I would love to figure out what the cause of this was but I doubt we shall ever know.

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

