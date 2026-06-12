---
title: "Terminal doesn't open on /home"
date: 2017-06-22
forum: General Help
---

### Post by damnporthos on 2017-06-22
I have changed my /home folder to another partition, in order to gain HD memory. The transfer occured without major issues and now, apparently, everything is working fine. Except for the bash.
When I open it with CTRL+ALT+T, instead of opening in /home as usually, it is opening in media/temp, an temporary folder used to store the (old) home's content before I moved it to the new one.

How can I set /home as default?

Prints: [http://imgur.com/a/rxbO7](http://imgur.com/a/rxbO7)

P.S.: I've already used some authentications methods (got it on the Internet) to see if /home is the *real* home; everything indicated yes, it is.

---

### Post by papibe on 2017-06-22
Hi damnporthos.

Have you logout and login again after the change?

Could you open run these commands and post back the results (you can copy/paste the text with your mouse, not need for pictures)?
```
mount -l

df -h

lsblk 

cat /etc/fstab 
```
Regards.

---

### Post by damnporthos on 2017-06-22
Hello, papibe. Thank you for the help

Yes, I have logged off already.

Here are the responses:
mount -l
```
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1945984k,nr_inodes=486496,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=393472k,mode=755)
/dev/sdb1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=31,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=12729)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda2 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda3 on /home type ext4 (rw,relatime,data=ordered)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
tmpfs on /run/user/121 type tmpfs (rw,nosuid,nodev,relatime,size=393472k,mode=700,uid=121,gid=127)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=393472k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
```

df -h
```
Filesystem      Size  Used Avail Use% Mounted on
udev            1,9G     0  1,9G   0% /dev
tmpfs           385M  6,5M  378M   2% /run
/dev/sdb1        19G  6,6G   12G  38% /
tmpfs           1,9G   16M  1,9G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           1,9G     0  1,9G   0% /sys/fs/cgroup
/dev/sda2       510M  3,4M  507M   1% /boot/efi
/dev/sda3       453G  1,6G  428G   1% /home
tmpfs           385M   12K  385M   1% /run/user/121
tmpfs           385M   36K  385M   1% /run/user/1000
```

lsblk
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdb      8:16   0  29,8G  0 disk 
&#9492;&#9472;sdb1   8:17   0  19,1G  0 part /
sda      8:0    0 465,8G  0 disk 
&#9500;&#9472;sda2   8:2    0   511M  0 part /boot/efi
&#9500;&#9472;sda3   8:3    0 459,6G  0 part /home
&#9492;&#9472;sda1   8:1    0   1,9G  0 part [SWAP]
```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=b1b43033-c18c-47eb-9ca2-66e81dd544b2 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=6771-D815  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda1 during installation
UUID=a851d32d-57c7-4c15-827c-7ccb63d4cf2a none            swap    sw              0       0
UUID=cf29bb00-11c4-40f0-bab8-aea7ff8cfd1d /home ext4 defaults 0 2
```

---

### Post by papibe on 2017-06-22
Thanks. Partitions and mount points look OK.

Let's check file permissions, in case in the move they got in disarray:
```
ls -la /home/ultrabook
ls -l /home/ultrabook/.bashrc
ls -l /home/ultrabook/.profile

```
Regards.

---

### Post by damnporthos on 2017-06-22
[B]ls -la /home/ultrabook
[/B]```
total 120drwxr-xr-x 24 ultrabook ultrabook 4096 Jun 22 21:56 .
drwxr-xr-x  4 root      root      4096 Jun 21 22:05 ..
drwx------  3 ultrabook ultrabook 4096 Jun 22 19:34 .adobe
-rw-------  1 ultrabook ultrabook 1626 Jun 22 21:57 .bash_history
-rw-r--r--  1 ultrabook ultrabook  220 Jun 21 22:19 .bash_logout
-rw-r--r--  1 ultrabook ultrabook 3771 Jun 21 22:19 .bashrc
drwx------ 21 ultrabook ultrabook 4096 Jun 22 19:34 .cache
drwx------ 25 ultrabook ultrabook 4096 Jun 22 19:36 .config
drwx------  3 ultrabook ultrabook 4096 Jun 22 19:36 .dbus
drwxr-xr-x  2 ultrabook ultrabook 4096 Jun 22 18:59 Desktop
drwxr-xr-x  2 ultrabook ultrabook 4096 Jun 21 22:31 Documents
drwxr-xr-x  2 ultrabook ultrabook 4096 Jun 22 15:12 Downloads
drwx------  2 ultrabook ultrabook 4096 Jun 22 21:07 .gconf
-rw-r-----  1 ultrabook ultrabook    0 Jun 22 11:49 .gksu.lock
drwx------  3 ultrabook ultrabook 4096 Jun 22 19:36 .gnome
drwx------  3 ultrabook ultrabook 4096 Jun 22 21:07 .gnupg
-rw-------  1 ultrabook ultrabook 2656 Jun 22 21:07 .ICEauthority
drwx------  3 ultrabook ultrabook 4096 Jun 22 18:59 .local
drwx------  3 ultrabook ultrabook 4096 Jun 22 19:36 .macromedia
drwx------  4 ultrabook ultrabook 4096 Jun 22 19:36 .mozilla
drwxrwxr-x  2 ultrabook ultrabook 4096 Jun 22 19:36 .mplayer
drwxr-xr-x  2 ultrabook ultrabook 4096 Jun 21 22:31 Music
drwxr-xr-x  3 ultrabook ultrabook 4096 Jun 22 20:38 Pictures
drwx------  3 ultrabook ultrabook 4096 Jun 22 19:00 .pki
-rw-r--r--  1 ultrabook ultrabook  655 Jun 21 22:19 .profile
drwxr-xr-x  2 ultrabook ultrabook 4096 Jun 21 22:31 Public
drwx------  2 ultrabook ultrabook 4096 Jun 21 23:18 .ssh
-rw-r--r--  1 ultrabook ultrabook    0 Jun 21 22:44 .sudo_as_admin_successful
drwxr-xr-x  2 ultrabook ultrabook 4096 Jun 21 22:31 Templates
drwxrwxr-x  3 ultrabook ultrabook 4096 Jun 22 19:36 .themes
drwxr-xr-x  2 ultrabook ultrabook 4096 Jun 21 22:31 Videos
-rw-rw-r--  1 ultrabook ultrabook  246 Jun 22 12:50 .wget-hsts
```

[B]ls -l /home/ultrabook/.bashrc
[/B]```
-rw-r--r-- 1 ultrabook ultrabook 3771 Jun 21 22:19 /home/ultrabook/.bashrc
```

**ls -l /home/ultrabook/.profile**
```
-rw-r--r-- 1 ultrabook ultrabook 655 Jun 21 22:19 /home/ultrabook/.profile
```

---

### Post by papibe on 2017-06-22
Thanks. Permissions look OK too.

Let's see if there's some unforeseen effects on an old modification to your login and bash files:
```
diff /etc/skel/.bashrc  ~/.bashrc

diff /etc/skel/.profile ~/.profile
```
Regards.

---

### Post by damnporthos on 2017-06-22
Both commands return nothing. There's no error message or stanby/processing time.

---

### Post by papibe on 2017-06-22
:(

What terminal client are you using? Do you have a custom command on the client's profile?

For instance, in gnome-terminal you can set one in:
```
Edit -> Profile Preferences -> Command
```

Is these behavior also happens when launching the terminal from a menu, or a launcher?

Regards.

---

### Post by damnporthos on 2017-06-22
I'm using the default terminal from Ubuntu Gnome 16.04.2 LTS. 

When running **Edit -> Profile Preferences -> Command **this is what I get:
```
No command 'Edit' found, did you mean: Command 'edit' from package 'mime-support' (main)
Edit: command not found
```

This behavior doesn't change when lauching the Terminal from a folder (with right click) nor from the dash. Strangely, when I run it through the dash it opens on the /home instead of media/temp.

---

### Post by vasa1 on 2017-06-22
@damnporthos, please use code tags instead of quote tags when including terminal content. Thanks.

---

### Post by papibe on 2017-06-22
That's on the GUI menu of gnome-terminal. Could you check that?

---

### Post by damnporthos on 2017-06-22
@vasa1, sorry for that. I didn't notice you were correcting my posts. Promess that I will pay more attention from now on.

@papibe, I'm sorry but I didn't undestand whay you meant. When I said *from the dash*, this is what I tried to express:[IMG]http://i.imgur.com/vaxvGew.jpg?3[/IMG]

---

### Post by papibe on 2017-06-22
The gnome terminal window has menus:
```
File Edit View Search Terminal Help
```
Click on Edit then Profile Preferences. When a new window opens, go to the tab Command.

Regards.

---

### Post by damnporthos on 2017-06-22
Checked. No *Custom Commands* - by the way, this field is currently disabled.  
Just in case, both *Run command as login shell* and *Run a custom command instead of my shell*&#8203; are unmarked.

---

### Post by Dennis N on 2017-06-22
You want bash in the terminal to use another folder as your home folder? If so, what is the full path to the folder you want to use as home?

---

### Post by damnporthos on 2017-06-23
Bash is opening default on media/temp. I want it to open on /home.

---

### Post by Dennis N on 2017-06-23
You said you moved your home to another partition. What is the mount point for that partition?

---

### Post by damnporthos on 2017-06-23
The /home partition is Ext4. (Sorry if this doesn't anwser your question but I dont really know what a *Mount Point*&#8203; is)

---

### Post by Dennis N on 2017-06-23
Let's try this: What output do you get when you type this in the terminal?

```
echo $HOME
```

Edit: Will check back later for any response. A TV show I watch is coming on now.

---

### Post by papibe on 2017-06-23
Have you installed another terminal emulator?

Could you run this command, and post back the options it gives you?
```
sudo update-alternatives --config x-terminal-emulator
```
You can press Enter to keep your current option.

Regards.

---

### Post by damnporthos on 2017-06-23
Sorry for being late. Today was a busy one.

Anyway, @Dennis N: after I ran your command the response was:
```
/home/ultrabook
```

@Papibe: no, I'm using the default one. Your command returns:
```
There are 5 choices for the alternative x-terminal-emulator (providing /usr/bin/x-terminal-emulator).

  Selection    Path                             Priority   Status
------------------------------------------------------------
* 0            /usr/bin/gnome-terminal.wrapper   40        auto mode
  1            /usr/bin/gnome-terminal.wrapper   40        manual mode
  2            /usr/bin/koi8rxterm               20        manual mode
  3            /usr/bin/lxterm                   30        manual mode
  4            /usr/bin/uxterm                   20        manual mode
  5            /usr/bin/xterm                    20        manual mode


Press <enter> to keep the current choice
[*], or type selection number: 
```

**EDIT:** After pressing enter, my screen got black and then returned to normal, but every applications was closed. I pressed CTRL+ALT+T and **now it's opening on /home**. Should I start believing in the Flying Spaghetti Monster?
Anyway, things seems to be okay now. Thank you, guys; you were very helpful.

---

### Post by Dennis N on 2017-06-23
The default directory for the terminal is the value of HOME, so your terminal should be opening to /home/ultrabook. I assume that is your actual home folder. Maybe the value got reset when you reconfigured the terminal. Glad you got it cleared up.

---

