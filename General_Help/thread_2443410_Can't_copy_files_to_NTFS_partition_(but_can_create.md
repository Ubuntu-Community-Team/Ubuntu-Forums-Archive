---
title: "Can't copy files to NTFS partition (but can create folders or rename files)"
date: 2020-05-15
forum: General Help
---

### Post by chinchulin on 2020-05-15
Hello everyone. 
I'm using an HD with 3 partitions: Windows 10, a large NTFS partition for storage and another ext4 partition for Ubuntu 20.04. 
I could copy files from my Ubuntu partition to the other two partitions but I can't do it anymore since this morning. 
I tried the recommendation of disabling hibernation on Windows and running chkdsk to no avail. 
I can create new folders in those partitions and change the names of existing files though.
Could anyone help me here?

Thanks in advance!

---

### Post by oldfred on 2020-05-15
Did Windows do an update. It may have been in background and you did not even see it.

Windows on updates often turns fast start up back on. That sets hibernation flag, so Ubuntu will not normally mount the NTFS partitions. They can be mounted read only.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by ActionParsnip on 2020-05-15
In Windows run a full chkdsk on the partition. The NTFS access you enjoy is a best effort attempt as NTFS is proprietary and only Microsoft knows how NTFS really works.
Making sure the file system is complete and consistent will help Ubuntu access it

---

### Post by Impavidus on 2020-05-15
A bit weird that you can create directories and rename stuff, but cannot copy files – but maybe you can create empty files? It looks like you've got read/write/execute access on directories, but only read access on the files. Something funny going on with dmask and fmask options? Check the mount options of that filesystem:```
findmnt /your/mountpoint

# For example:
findmnt /media/user/winpartition
```

---

### Post by chinchulin on 2020-05-15
Thanks everyone for the quick responses! I don't think it has anything to do with Windows: I tried copying one file from my phone to my storage partition and it worked without a hitch. On the other hand I noticed I can't move files around inside Ubuntu. I get a circle with a diagonal stripe when I start to drag any file. Please see picture attached: 

[IMG]https://i.imgur.com/nADV9eOl.jpg[/IMG]

---

### Post by TheFu on 2020-05-15
Doubt i can help.  Not seeing any of the questions asked above by others getting answered.  impossible to help without having questions answered.

NTFS mounts set the permissions at mount time.  So that's why the **findmnt** command was requested.
Seeing the permissions after the mount would be helpful too.  That's a **ls -al /path/to/files**

Please help us to help you by running those commands, modified for your system and directories, then posting the results / output back here.  Using 'code tags' for the command+output would be extra nice.  Hard to read posts get fewer eyes and interpretations can be wrong.

Please.

---

### Post by chinchulin on 2020-05-17
> **TheFu said:**
> Doubt i can help.  Not seeing any of the questions asked above by others getting answered.  impossible to help without having questions answered.

NTFS mounts set the permissions at mount time.  So that's why the **findmnt** command was requested.
Seeing the permissions after the mount would be helpful too.  That's a **ls -al /path/to/files**

Please help us to help you by running those commands, modified for your system and directories, then posting the results / output back here.  Using 'code tags' for the command+output would be extra nice.  Hard to read posts get fewer eyes and interpretations can be wrong.

Please.
Hi! Thanks for your reply. This is the output of **findmnt:**

TARGET                                SOURCE      FSTYPE  OPTIONS
/                                     /dev/sda6   ext4    rw,relatime,errors=rem
&#9500;&#9472;/sys                                sysfs       sysfs   rw,nosuid,nodev,noexec
&#9474; &#9500;&#9472;/sys/kernel/security              securityfs  securit rw,nosuid,nodev,noexec
&#9474; &#9500;&#9472;/sys/fs/cgroup                    tmpfs       tmpfs   ro,nosuid,nodev,noexec
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/unified          cgroup2     cgroup2 rw,nosuid,nodev,noexec
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/systemd          cgroup      cgroup  rw,nosuid,nodev,noexec
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/cpuset           cgroup      cgroup  rw,nosuid,nodev,noexec
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/perf_event       cgroup      cgroup  rw,nosuid,nodev,noexec
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/devices          cgroup      cgroup  rw,nosuid,nodev,noexec
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/blkio            cgroup      cgroup  rw,nosuid,nodev,noexec
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/cpu,cpuacct      cgroup      cgroup  rw,nosuid,nodev,noexec
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/freezer          cgroup      cgroup  rw,nosuid,nodev,noexec
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/net_cls,net_prio cgroup      cgroup  rw,nosuid,nodev,noexec
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/hugetlb          cgroup      cgroup  rw,nosuid,nodev,noexec
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/rdma             cgroup      cgroup  rw,nosuid,nodev,noexec
&#9474; &#9474; &#9500;&#9472;/sys/fs/cgroup/memory           cgroup      cgroup  rw,nosuid,nodev,noexec
&#9474; &#9474; &#9492;&#9472;/sys/fs/cgroup/pids             cgroup      cgroup  rw,nosuid,nodev,noexec
&#9474; &#9500;&#9472;/sys/fs/pstore                    pstore      pstore  rw,nosuid,nodev,noexec
&#9474; &#9500;&#9472;/sys/fs/bpf                       none        bpf     rw,nosuid,nodev,noexec
&#9474; &#9500;&#9472;/sys/kernel/debug                 debugfs     debugfs rw,nosuid,nodev,noexec
&#9474; &#9500;&#9472;/sys/kernel/tracing               tracefs     tracefs rw,nosuid,nodev,noexec
&#9474; &#9500;&#9472;/sys/fs/fuse/connections          fusectl     fusectl rw,nosuid,nodev,noexec
&#9474; &#9492;&#9472;/sys/kernel/config                configfs    configf rw,nosuid,nodev,noexec
&#9500;&#9472;/proc                               proc        proc    rw,nosuid,nodev,noexec
&#9474; &#9492;&#9472;/proc/sys/fs/binfmt_misc          systemd-1   autofs  rw,relatime,fd=28,pgrp
&#9500;&#9472;/dev                                udev        devtmpf rw,nosuid,noexec,relat
&#9474; &#9500;&#9472;/dev/pts                          devpts      devpts  rw,nosuid,noexec,relat
&#9474; &#9500;&#9472;/dev/shm                          tmpfs       tmpfs   rw,nosuid,nodev
&#9474; &#9500;&#9472;/dev/mqueue                       mqueue      mqueue  rw,nosuid,nodev,noexec
&#9474; &#9492;&#9472;/dev/hugepages                    hugetlbfs   hugetlb rw,relatime,pagesize=2
&#9500;&#9472;/run                                tmpfs       tmpfs   rw,nosuid,nodev,noexec
&#9474; &#9500;&#9472;/run/lock                         tmpfs       tmpfs   rw,nosuid,nodev,noexec
&#9474; &#9500;&#9472;/run/snapd/ns                     tmpfs[/snapd/ns]
&#9474; &#9474;                                               tmpfs   rw,nosuid,nodev,noexec
&#9474; &#9474; &#9492;&#9472;/run/snapd/ns/snap-store.mnt    nsfs[mnt:[4026532522]]
&#9474; &#9474;                                               nsfs    rw
&#9474; &#9492;&#9472;/run/user/1000                    tmpfs       tmpfs   rw,nosuid,nodev,relati
&#9474;   &#9500;&#9472;/run/user/1000/doc              /dev/fuse   fuse    rw,nosuid,nodev,relati
&#9474;   &#9492;&#9472;/run/user/1000/gvfs             gvfsd-fuse  fuse.gv rw,nosuid,nodev,relati
&#9500;&#9472;/snap/core18/1754                   /dev/loop1  squashf ro,nodev,relatime
&#9500;&#9472;/snap/core/9066                     /dev/loop3  squashf ro,nodev,relatime
&#9500;&#9472;/snap/gtk2-common-themes/9          /dev/loop6  squashf ro,nodev,relatime
&#9500;&#9472;/snap/gnome-3-34-1804/27            /dev/loop2  squashf ro,nodev,relatime
&#9500;&#9472;/snap/core18/1705                   /dev/loop0  squashf ro,nodev,relatime
&#9500;&#9472;/snap/gtk-common-themes/1506        /dev/loop5  squashf ro,nodev,relatime
&#9500;&#9472;/snap/gnome-3-34-1804/33            /dev/loop4  squashf ro,nodev,relatime
&#9500;&#9472;/snap/snapd/7264                    /dev/loop9  squashf ro,nodev,relatime
&#9500;&#9472;/snap/snap-store/433                /dev/loop8  squashf ro,nodev,relatime
&#9500;&#9472;/snap/vlc/1620                      /dev/loop10 squashf ro,nodev,relatime
&#9492;&#9472;/snap/p7zip-desktop/220             /dev/loop7  squashf ro,nodev,relatime




This is the output of **ls -al **for the folder "linux" in my desktop (it's just an example, I can't drag and drop any other file):

heidi@heidi-desktop:~$ ls -al /home/heidi/Desktop/linux
total 28
drwxrwxr-x 4 heidi heidi 4096 may 15 18:02 .
drwxrwxr-x 3 heidi heidi 4096 may 15 18:36 ..
drwxrwxr-x 2 heidi heidi 4096 may 12 13:07 app
-rwxrwxr-x 1 heidi heidi  590 may 12 13:07 install.sh
drwxrwxr-x 4 heidi heidi 4096 may 12 13:07 node
-rw-rw-r-- 1 heidi heidi  370 may 12 13:07 ReadMe.txt
-rwxrwxr-x 1 heidi heidi 1216 may 12 13:07 uninstall.sh



As stated in my previous post, the issue doesn't seem to be Windows related, since I can't drag and drop files within Ubuntu. Well, it does work if I drag the file from whichever the folder (Downloads in this case) to the directories on the  left column (red arrow with green check). It doesn't work if I drag it to the Desktop itself (red arrow with red cross). Dragging from the Desktop to the directories in the grey column or the Downloads folder doesn't work at all. I get the circle with the diagonal stripe as per my previous post.

[IMG]https://i.imgur.com/9G9VrxS.jpg[/IMG]

---

### Post by CelticWarrior on 2020-05-17
Your thread starts with:
> (...)
I could copy files from my Ubuntu partition to the other two partitions but I can't do it anymore since this morning. 
I tried the recommendation of disabling hibernation on Windows and running chkdsk to no avail. 
I can create new folders in those partitions and change the names of existing files though.
This has absolutely nothing to do with copying files to your desktop. BTW, you can't now, by design, and for reasons you may ask Gnome devs.
And that "Desktop" folder you're showing is NOT your desktop. That's how things are now with Gnome.
Again, this has nothing to do with copying files to NTFS partitions.

---

### Post by TheFu on 2020-05-17
I have no idea whether dropping files outside the file manager should work or not. Wouldn't assume that an X11 "desktop" would accept a file being dropped in this way.  I don't use file managers much. Much too slow.

The important parts are these:

```
/ /dev/sda6 ext4 rw,relatime,errors=rem
```
and 
```
$ ls -al /home/heidi/Desktop/linux
total 28
drwxrwxr-x 4 heidi heidi 4096 may 15 18:02 .
drwxrwxr-x 3 heidi heidi 4096 may 15 18:36 ..
```

That shows that the file system is mounted read-write
and the permissions for "Desktop/" should allow username "heidi" to create files there.

Failures for that directory would be:
[LIST]
[*]Full storage
[*]Full inodes
[*]Some security constraint from a snap package or apparmor
[*]failing storage
[/LIST]

Out of storage?
```
df -Th /
df -Ti /

```
Would be helpful if all the snap/loop mounts weren't included.  There are options to not show that ... 
```
df -hT -x squashfs -x tmpfs -x devtmpfs /
```

Check the system logs in /var/log/ for any warnings or errors related to permissions, denied, failure, reject ... stuff like that.
For storage issues, I'd look at SMART data.
```
sudo smartctl -t short /dev/sda
```
wait however long the output says. Then to see the test results run:
```
sudo smartctl -a  /dev/sda
```

See how I've used code tags?  With lots of terminal output, it is much easier to read. Please use **code tags.**

---

