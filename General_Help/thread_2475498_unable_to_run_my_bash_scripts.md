---
title: "unable to run my bash scripts"
date: 2022-05-29
forum: General Help
---

### Post by coley9225 on 2022-05-29
I just began having an issue with most of my bash scripts. I have run them many times before, so it isn't the script itself. 
when I try to run run one, I get 'permission denied'. I have check executability, ownership, even verified I'm running a bash shell. Same error running with sudo and from root shell. I even tried from tty console.

This ls -Al from one of my directories.
```
harles:$ lltotal 48
-rwxrwxr-x 1 charles charles 1338 May 29 13:33 add_with_cowsay.sh*
-rwxr-xr-x 1 charles charles 1827 Jul 24  2021 add_with_timeout.sh*
-rwxrwxr-x 1 charles charles 1545 May 28 17:15 copy_files.sh*
-rwxrwxr-x 1 charles charles 1016 Oct 16  2021 dividing_quiz.sh*
-rwxr-xr-x 1 charles charles 8145 Nov 13  2021 multi_level_math_quiz.sh*
-rw-rw-r-- 1 charles charles  463 Nov 23  2021 right_answer.txt
-rw-rw-r-- 1 charles charles  424 Dec 10  2020 save_the_day.txt
-rw-rw-r-- 1 charles charles 1125 Nov 14  2021 tar_incre_backup.sh
-rwxrwxr-x 1 charles charles  847 Aug 12  2021 testing.sh*
-rwxr-xr-x 1 charles charles  407 Nov 23  2020 test_script.sh*
-rw-rw-r-- 1 charles charles  264 Apr 15 13:36 wrong_answer.txt
charles:$ 

```

You can see that I am the owner. Again, I have run every one of these many times before. when I try to run one, with multiple methods.
```
charles:$ ./add_with_cowsay.shbash: ./add_with_cowsay.sh: Permission denied
charles:$ sudo ./add_with_cowsay.sh
[sudo] password for charles: 
sudo: unable to execute ./add_with_cowsay.sh: Permission denied
charles:$ sudo -i
root:# ./add_with_cowsay.sh
-bash: ./add_with_cowsay.sh: Permission denied
root:# 




```

This just one of many scripts I have. Almost all do the same. I can run my update.sh, but I am at a total loss as to where to turn from here to get the rest of my scripts running again.
Any ideas on what to try? If you need more info, I'll be watching this thread closely, just ask.
Thank you so much for any help you can be.

---

### Post by Bashing-om on 2022-05-29
coley9225; Hello

The question that pops to my mind is "who" owns all the directories in the paths to your script locations ?
Has a directory ownership changed sometime along the line ?

[INDENT]keep on the straight $PATH
[/INDENT]

---

### Post by coley9225 on 2022-05-29
Bashing-om. I am the only user on the computer. I checked everything from /home/charles down, and I own it all. Even if ownership had somehow changed, I should still be able to run with sudo, or from root prompt, if I understand any of it at all.
I tried to do a release upgrade, which went sideways on me. I restore from timeshift back to the point about 30 minutes prior to the upgrade. I did not run any scripts in the day or so before that, so not  sure if this started just before or because of the failed upgrade. Like I said, I have an update script that runs fine. I can also use sudo with not problems(sudo apt update, sudo mkdir /home/newdir, etc), I just can't run my scripts, which have been run many time before. I am, at this point, totally lost, dazed and confused.

Any thoughts or ideas? I could really use some help on this one.

I just double checked ownership, and I do own all the directories from my home dir down, except for a couple I intentionally made root the owner.

---

### Post by &amp;KyT$0P# on 2022-05-29
Is the filesystem containing those scripts somehow got mounted with [FONT=Courier New]noexec[/FONT] option?
```
findmnt | less
```

---

### Post by coley9225 on 2022-05-29
halogen2, I'm not sure what I'm looking at, or for. Output below.

findmnt | less
```
TARGET                                                SOURCE                 FSTYPE          OPTIONS/                                                     /dev/sda2              ext4            rw,relatime,discard
&#9500;&#9472;/sys                                                sysfs                  sysfs           rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/kernel/security                              securityfs             securityfs      rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/fs/cgroup                                    tmpfs                  tmpfs           ro,nosuid,nodev,noexec,mode=755,inode64
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/unified                          cgroup2                cgroup2         rw,nosuid,nodev,noexec,relatime,nsdelegate
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/systemd                          cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,xattr,name=systemd
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/rdma                             cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,rdma
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/perf_event                       cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,perf_event
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/memory                           cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,memory
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/pids                             cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,pids
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/hugetlb                          cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,hugetlb
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/devices                          cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,devices
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/net_cls,net_prio                 cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,net_cls,net_prio
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/freezer                          cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,freezer
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/cpu,cpuacct                      cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,cpu,cpuacct
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/blkio                            cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,blkio
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/cpuset                           cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,cpuset
&#9474; &#9474; &#9492;&#9472;/sys/fs/cgroup/misc                             cgroup                 cgroup          rw,nosuid,nodev,noexec,relatime,misc
&#9474; &#9500;&#9472;/sys/fs/pstore                                    pstore                 pstore          rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/firmware/efi/efivars                         efivarfs               efivarfs        rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/fs/bpf                                       none                   bpf             rw,nosuid,nodev,noexec,relatime,mode=700
&#9474; &#9500;&#9472;/sys/kernel/debug                                 debugfs                debugfs         rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/kernel/tracing                               tracefs                tracefs         rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/kernel/config                                configfs               configfs        rw,nosuid,nodev,noexec,relatime
&#9474; &#9492;&#9472;/sys/fs/fuse/connections                          fusectl                fusectl         rw,nosuid,nodev,noexec,relatime
&#9500;&#9472;/proc                                               proc                   proc            rw,nosuid,nodev,noexec,relatime
&#9474; &#9492;&#9472;/proc/sys/fs/binfmt_misc                          systemd-1              autofs          rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=18408
&#9500;&#9472;/dev                                                udev                   devtmpfs        rw,nosuid,noexec,relatime,size=3921908k,nr_inodes=980477,mode=755,inode64
&#9474; &#9500;&#9472;/dev/pts                                          devpts                 devpts          rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000
&#9474; &#9500;&#9472;/dev/shm                                          tmpfs                  tmpfs           rw,nosuid,nodev,inode64
&#9474; &#9500;&#9472;/dev/hugepages                                    hugetlbfs              hugetlbfs       rw,relatime,pagesize=2M
&#9474; &#9492;&#9472;/dev/mqueue                                       mqueue                 mqueue          rw,nosuid,nodev,noexec,relatime
&#9500;&#9472;/run                                                tmpfs                  tmpfs           rw,nosuid,nodev,noexec,relatime,size=796232k,mode=755,inode64
&#9474; &#9500;&#9472;/run/lock                                         tmpfs                  tmpfs           rw,nosuid,nodev,noexec,relatime,size=5120k,inode64
&#9474; &#9500;&#9472;/run/snapd/ns                                     tmpfs[/snapd/ns]       tmpfs           rw,nosuid,nodev,noexec,relatime,size=796232k,mode=755,inode64
&#9474; &#9474; &#9492;&#9472;/run/snapd/ns/canonical-livepatch.mnt           nsfs[mnt:[4026532615]] nsfs            rw
&#9474; &#9500;&#9472;/run/timeshift/backup                             /dev/sdb2              ext4            rw,relatime
&#9474; &#9492;&#9472;/run/user/1000                                    tmpfs                  tmpfs           rw,nosuid,nodev,relatime,size=796228k,mode=700,uid=1000,gid=1001,inode64
&#9474;   &#9500;&#9472;/run/user/1000/doc                              /dev/fuse              fuse            rw,nosuid,nodev,relatime,user_id=1000,group_id=1001
&#9474;   &#9492;&#9472;/run/user/1000/gvfs                             gvfsd-fuse             fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=1000,group_id=1001
&#9500;&#9472;/snap/canonical-livepatch/132                       /dev/loop0             squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/canonical-livepatch/138                       /dev/loop1             squashfs        ro,nodev,relatime
&#9500;&#9472;/tmp                                                tmpfs                  tmpfs           rw,noatime,inode64
&#9500;&#9472;/snap/core/12834                                    /dev/loop2             squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/snapd/15904                                   /dev/loop4             squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/core18/2344                                   /dev/loop3             squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/snapd/15534                                   /dev/loop5             squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/core/13250                                    /dev/loop6             squashfs        ro,nodev,relatime
&#9500;&#9472;/snap/core18/2409                                   /dev/loop7             squashfs        ro,nodev,relatime
&#9500;&#9472;/var/lib/libvirt/images                             /dev/sda5              ext4            rw,nosuid,nodev,noexec,relatime
&#9500;&#9472;/boot/efi                                           /dev/sda1              vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
&#9500;&#9472;/home                                               /dev/sda4              ext4            rw,relatime,discard
&#9474; &#9500;&#9472;/home/charles/.Shared_files                       /dev/sda6              ext4            rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/home/charles/.B-I-T_backups                      /dev/sdb3              ext4            rw,nosuid,nodev,relatime
&#9474; &#9500;&#9472;/home/charles/.File_backup_copies                 /dev/sdb1              ext4            rw,nosuid,nodev,relatime
&#9474; &#9492;&#9472;/home/rsync                                       /dev/sdb4              ext4            rw,relatime
&#9500;&#9472;/root/.cache/gvfs                                   gvfsd-fuse             fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=0,group_id=0
&#9500;&#9472;/root/.cache/doc                                    /dev/fuse              fuse            rw,nosuid,nodev,relatime,user_id=0,group_id=0
&#9500;&#9472;/media/charles/Media_backups                        /dev/sdb6              ext4            rw,nosuid,nodev,relatime
&#9492;&#9472;/media/charles/01327e3d-1085-4caa-8b09-676def8dccef /dev/sdb2              ext4            rw,nosuid,nodev,relatime



```

And my fstab file.

```
# <file system> <mount point> <type> <options> <dump> <pass>

UUID=c95e8489-2208-4b25-b12f-69aaaf3d28c1	/	ext4	defaults,discard	0	1
UUID=58ba0a88-2497-462c-bb42-02eb4e7ffbae	/home	ext4	defaults,discard	0	2
tmpfs	/tmp	tmpfs	defaults,noatime,mode=1777	0	0
UUID=0210-7AA4	/boot/efi	vfat	defaults	0	1
UUID=891055ad-c8c6-431f-b969-8ca5c160516e	/home/charles/.B-I-T_backups	ext4	user,auto,exec,rw,async	0	0
UUID=c23e8deb-98eb-437a-834f-7a9287937dc0	/var/lib/libvirt/images	ext4	auto,rw,async,user,discard	0	0
UUID=d09e1165-75e2-424f-ada5-f3e9c11ff1e6	/home/charles/.Shared_files	ext4	auto,rw,async,user,discard,exec	0	0


UUID=01284c07-a5ca-43fc-9cea-6b790910f8c9  /home/charles/.File_backup_copies ext4  user,auto,exec,rw	0	0


UUID=f9f0c159-7eaa-457a-b179-2d3701b9302b  /home/rsync  ext4  noauto,rw,exec	0	0

```

The 'B-I-T_backups' is the mount point for external partition for my back in time backups. Owned by root, so I don't inadvertently delete anything.

As I said, I haven't a clue what I'm looking at or for, but you see an issue, please point it out and explain how to fix it.

---

### Post by &amp;KyT$0P# on 2022-05-29
Without knowing the full real path to your scripts, I'm not sure what we're looking for either, but -
> **coley9225 said:**
> ```

&#9474; &#9500;&#9472;/home/charles/.Shared_files                       /dev/sda6              ext4            rw,nosuid,nodev,[COLOR="#FF0000"]**noexec**[/COLOR],relatime

```
(emphasis mine)

Are your scripts stored under [FONT=Courier New]/home/charles/.Shared_files[/FONT] ?

---

### Post by coley9225 on 2022-05-29
I sat here for a few minutes and thought about it, and I should note that the findmnt was run after I add exec to .Shared_files. I thought maybe I have to reboot for that change to be effective. I rebooted my computer and tried a couple of scripts, and they ran. Apparently, it was set to noexec before, and changing it solved the problem.

I made the .Shared_files mount point, and made the new partition, because I want to add a new distro, and wanted to share the files. I neglected to add the exec option when I made the fstab entry.

I would have pulled my hair out and then some, and never found this without the tip to check findmnt. I will make as solved.

As always, thanks so much for the help.

---

