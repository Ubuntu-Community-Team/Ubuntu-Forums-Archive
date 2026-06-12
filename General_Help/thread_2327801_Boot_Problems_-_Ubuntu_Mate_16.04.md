---
title: "Boot Problems - Ubuntu Mate 16.04"
date: 2016-06-14
forum: General Help
---

### Post by mcmarius2 on 2016-06-14
[COLOR=#111111][FONT=Ubuntu]Hi,
I have some serious boot problems. When I boot my ThinkPad T450s I can unlock my drive using normal Ubuntu password encryption. Then I get a kind of terminal (or shell, I guess its the same) and I can login myself. I figured out that I can boot when I type[/FONT][/COLOR]
```
sudo mount -o remount,rw /
sudo mount -a
sudo lightdm
```
[COLOR=#111111][FONT=Ubuntu]I checked the boot.log in /var/log:[/FONT][/COLOR]
```
lvmetad is not active yet, using direct activation during sysinit
  Volume group "ubuntu-mate-vg" not found
  Cannot process volume group ubuntu-mate-vg
  /run/lvm/lvmetad.socket: connect failed: No such file or directory
  WARNING: Failed to connect to lvmetad. Falling back to internal scanning.
  Reading all physical volumes.  This may take a while...
  Found volume group "ubuntu-mate-vg" using metadata type lvm2
  /run/lvm/lvmetad.socket: connect failed: No such file or directory
  WARNING: Failed to connect to lvmetad. Falling back to internal scanning.
  2 logical volume(s) in volume group "ubuntu-mate-vg" now active
  /dev/mapper/ubuntu--mate--vg-root: clean, 657327/14786560 files, 34622765/59141120 blocks
```
[COLOR=#111111][FONT=Ubuntu]So I guess there is something wrong in my fstab:[/FONT][/COLOR]
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# /boot was on /dev/sda2 during installation
UUID=b14a41f2-a23b-494a-9524-f01ae898d61e /boot           ext2    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=BFC3-1A74  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/ubuntu--mate--vg-swap_1 none            swap    sw              0       0
```
[COLOR=#111111][FONT=Ubuntu]but I'm not that good on Ubuntu to figure out whtas wrong.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I also checked the the volume group by typing[/FONT][/COLOR]
```
sudo lvdisplay
```
[COLOR=#111111][FONT=Ubuntu]Output:[/FONT][/COLOR]
  ```
--- Logical volume ---
  LV Path                /dev/ubuntu-mate-vg/root
  LV Name                root
  VG Name                ubuntu-mate-vg
  LV UUID                AsKTiD-ZGwk-7B9o-XWLt-rEMZ-usiM-TSK2uo
  LV Write Access        read/write
  LV Creation host, time ubuntu-mate, 2016-05-10 08:13:22 +0200
  LV Status              available
  # open                 1
  LV Size                225,61 GiB
  Current LE             57755
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

  --- Logical volume ---
  LV Path                /dev/ubuntu-mate-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-mate-vg
  LV UUID                lJDLAc-sd6q-mJff-6Ds2-KrlK-sXSm-xxdoDw
  LV Write Access        read/write
  LV Creation host, time ubuntu-mate, 2016-05-10 08:13:22 +0200
  LV Status              available
  # open                 2
  LV Size                11,88 GiB
  Current LE             3041
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
```
[COLOR=#111111][FONT=Ubuntu]Using pvs:[/FONT][/COLOR]
```
marius@marius-ThinkPad-T450s:~/Schreibtisch$ sudo pvs
  PV                     VG             Fmt  Attr PSize   PFree
  /dev/mapper/sda3_crypt ubuntu-mate-vg lvm2 a--  237,49g 8,00m
```
[COLOR=#111111][FONT=Ubuntu]I hope someone can help because I dont want to install everything new. If you need further information please let me know![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks in advance mcmarius[/FONT][/COLOR]

---

### Post by QDR06VV9 on 2016-06-14
Not sure I can help, but are you dual booting windows with ubuntu?

---

### Post by mcmarius2 on 2016-06-14
No, just Ubuntu Mate.

---

### Post by QDR06VV9 on 2016-06-14
What is the out put of this in the terminal
```
sudo blkid
```

---

### Post by ajgreeny on 2016-06-14
I have never used encryption but I notice that your fstab has no entry for a root partition which I think must be a problem when it tries to boot.

However you say that you can get to a system with you logged in so there must be a root partition; I am just baffled why it does not show in fstab, but perhaps that is because you have encryption.  

Just something to think about?

---

### Post by mcmarius2 on 2016-06-14
> **runrickus said:**
> What is the out put of this in the terminal
```
sudo blkid
```

```
/dev/mapper/sda3_crypt: UUID="lviW2P-U6ng-9ZJW-V8ls-TSNn-EOCN-MIBTXg" TYPE="LVM2_member"
/dev/mapper/ubuntu--mate--vg-root: UUID="57e13c75-8798-4169-b095-243b3049b248" TYPE="ext4"
/dev/sda1: UUID="BFC3-1A74" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="3e2529e1-788c-4ba1-b8c9-bdc0ff144e8b"
/dev/sda2: UUID="b14a41f2-a23b-494a-9524-f01ae898d61e" TYPE="ext2" PARTUUID="35c3fedc-7ea8-40cb-be42-3c399ff1a73a"
/dev/sda3: UUID="8c6fe08a-66ab-40fa-8741-16ae2d55ae4a" TYPE="crypto_LUKS" PARTUUID="7bb71f41-ba05-4b66-a9d9-5bf2015f97e3"
/dev/sdb1: LABEL="Eigene Daten" UUID="ff77263c-935d-4f57-b6b1-c5f8f0024aaf" TYPE="ext4" PARTUUID="f0a50b28-862b-45ab-a3ec-a75029ebb81e"
/dev/sdc1: LABEL="MJRO1606" UUID="6C66-6D5F" TYPE="vfat" PARTUUID="002d4599-01"
/dev/mapper/ubuntu--mate--vg-swap_1: UUID="9106fd6d-e608-42ea-ba21-4c9dee283b84" TYPE="swap"

```

---

### Post by mcmarius2 on 2016-06-14
> **ajgreeny said:**
> I have never used encryption but I notice that your fstab has no entry for a root partition which I think must be a problem when it tries to boot.

However you say that you can get to a system with you logged in so there must be a root partition; I am just baffled why it does not show in fstab, but perhaps that is because you have encryption.  

Just something to think about?

Yes...I thought about it too. I tried to add but it never works :/ may be with the ```
sudo blkid
``` someone could say if its definitely the reason.

---

### Post by QDR06VV9 on 2016-06-14
Yep I am afraid with encryption involved this going to be past my known skill level.
I have seen a lot of threads in other forums with similar requests and no solutions posted.
I would hate to give you an ill advised reply.

---

### Post by ajgreeny on 2016-06-14
Maybe this line is your root partition; as I say I do not use encryption so I have no idea how it normally shows in such a system
```
/dev/mapper/ubuntu--mate--vg-root: UUID="57e13c75-8798-4169-b095-243b3049b248" TYPE="ext4"
```
However, if it is the root partition it certainly is not in the fstab.

Once you have the system up and running with your workaround can you show us the output of command ```
mount
```which might give us more clues, though I'm not even certain if that will give us any more helpful info as **blkid** should have also told us all the partitions.

---

### Post by mcmarius2 on 2016-06-14
> **runrickus said:**
> Yep I am afraid with encryption involved this going to be past my known skill level.
I have seen a lot of threads in other forums with similar requests and no solutions posted.
I would hate to give you an ill advised reply.

But if i need to edit fstab and you have a suggestion then i can backup fstab and change it with livesytsem from my usb-drive.

---

### Post by mcmarius2 on 2016-06-14
> **ajgreeny said:**
> Maybe this line is ypour root partition; as I say I do not have encryption so I have no idea how it normally shows in such a system
```
/dev/mapper/ubuntu--mate--vg-root: UUID="57e13c75-8798-4169-b095-243b3049b248" TYPE="ext4"
```
However, if it is the root partition it certainly is not in the fstab.

Once you have the system up and running with your workaround can you show us the output of command ```
mount
```

```

sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=6069704k,nr_inodes=1517426,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1218016k,mode=755)
/dev/mapper/ubuntu--mate--vg-root on / type ext4 (rw,relatime,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd,nsroot=/)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices,nsroot=/)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,nsroot=/)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids,nsroot=/)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,nsroot=/)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct,nsroot=/)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer,nsroot=/)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory,nsroot=/)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,nsroot=/)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio,nsroot=/)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio,nsroot=/)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=35,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda2 on /boot type ext2 (rw,relatime,block_validity,barrier,user_xattr,acl)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1218016k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdc1 on /media/marius/MJRO1606 type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)

```

---

### Post by QDR06VV9 on 2016-06-14
Well lets see how it looks
```
pluma /etc/fstab 
```
Paste back the return

---

### Post by mcmarius2 on 2016-06-14
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# /boot was on /dev/sda2 during installation
UUID=b14a41f2-a23b-494a-9524-f01ae898d61e /boot           ext2    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=BFC3-1A74  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/ubuntu--mate--vg-swap_1 none            swap    sw              0       0
/dev/mapper/ubuntu--mate--vg-root: UUID="57e13c75-8798-4169-b095-243b3049b248" TYPE="ext4"
```

---

### Post by QDR06VV9 on 2016-06-14
I think this is line you want to add <[B]UUID="57e13c75-8798-4169-b095-243b3049b248" TYPE="ext4">
EDIT: here is some good info to refernce: [/B][http://askubuntu.com/questions/271516/is-there-a-program-to-mount-all-of-my-drives-automatically](http://askubuntu.com/questions/271516/is-there-a-program-to-mount-all-of-my-drives-automatically)

---

### Post by ajgreeny on 2016-06-14
You are now showing one extra line in fstab compared with your opening post.
```
/dev/mapper/ubuntu--mate--vg-root: UUID="57e13c75-8798-4169-b095-243b3049b248" TYPE="ext4"
```
Did you add than manually this time or was it missing from your first copy/paste?

I can still not help with how an encrypted fstab should look but in a normal system the root line would be 
```
UUID=57e13c75-8798-4169-b095-243b3049b248 /               ext4    errors=remount-ro 0       1
```
Perhaps worth a try, though I think the encryption will probably mean that is incorrect.

Why not edit the fstab file and then run command ```
sudo mount -a
``` which will throw back an error if the syntax is now wrong, and as you say, you can always backup the file and then restore it with a live system if you need to.

---

### Post by mcmarius2 on 2016-06-14
> **ajgreeny said:**
> You are now showing one extra line in fstab compared with your opening post.
```
/dev/mapper/ubuntu--mate--vg-root: UUID="57e13c75-8798-4169-b095-243b3049b248" TYPE="ext4"
```
Did you add than manually this time or was it missing from your first copy/paste?

I can still not help with how an encrypted fstab should look but in a normal system the root line would be 
```
UUID=57e13c75-8798-4169-b095-243b3049b248 /               ext4    errors=remount-ro 0       1
```
Perhaps worth a try, though I think the encryption will probably mean that is incorrect.

Why not edit the fstab file and then run command ```
sudo mount -a
``` which will throw back an error if the syntax is now wrong, and as you say, you can always backup the file and then restore it with a live system if you need to.

No, I manually added it but indeed it was wrong. 
Now i added ```
UUID=57e13c75-8798-4169-b095-243b3049b248 /               ext4    errors=remount-ro 0       1
``` 
After I tried 
```
sudo mount -a
```
without any error. Now i will try to reboot.

---

### Post by mcmarius2 on 2016-06-14
Well......you are definitely my hero today ajgreeny! It works! I added the line you suggested and now it solved! Thank you so much! 
Is there a thumbs up button /thanks button anywhere?

---

### Post by ajgreeny on 2016-06-15
Wonderful!

No there is not "Thanks" button but your comment above is all that I or anyoine else needs.  I am very happy that we managed to get it sorted out.

---

