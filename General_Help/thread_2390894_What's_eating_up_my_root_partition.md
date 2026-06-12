---
title: "What's eating up my root partition?"
date: 2018-05-03
forum: General Help
---

### Post by bogoliubov on 2018-05-03
Hi there. I can't upgrade to 18.04 since it turns out I do not have enough space on /. However, when I started to look at what takes up all the space, there seems to be something strange going on:


```
christian@x220:/$ sudo du -h --max-depth=1 | sort -h
du: kan inte komma åt './proc/17724/task/17724/fd/4': Filen eller katalogen finns inte
du: kan inte komma åt './proc/17724/task/17724/fdinfo/4': Filen eller katalogen finns inte
du: kan inte komma åt './proc/17724/fd/3': Filen eller katalogen finns inte
du: kan inte komma åt './proc/17724/fdinfo/3': Filen eller katalogen finns inte
du: kan inte komma åt './run/user/1000/gvfs': Åtkomst nekas
0	./cdrom
0	./media
0	./mnt
0	./opt
0	./proc
0	./srv
0	./sys
4,0K	./lib64
4,0K	./snap
28K	./root
1,5M	./run
5,6M	./dev
14M	./sbin
15M	./bin
18M	./etc
23M	./tmp
258M	./boot
681M	./var
1,2G	./lib
6,3G	./usr
198G	./home
206G	.

```

So about 8 GB is used by /.
But df reports this:

```

christian@x220:/$ df -h
Filsystem      Storlek Använt Ledigt Anv% Monterat på
udev              3,9G      0   3,9G   0% /dev
tmpfs             786M   1,4M   785M   1% /run
/dev/sda1          23G    17G   4,5G  80% /
tmpfs             3,9G    43M   3,8G   2% /dev/shm
tmpfs             5,0M   4,0K   5,0M   1% /run/lock
tmpfs             3,9G      0   3,9G   0% /sys/fs/cgroup
/dev/sda6         272G   198G    75G  73% /home
tmpfs             786M    56K   786M   1% /run/user/1000

```

So there seems to be 9 GB used that cannot be found. Any explanation for this?

---

### Post by oldfred on 2018-05-03
Deleted files not fully deleted but in root's trash?

       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

A while back I had issues deleting trash in root and had to temporarily give myself ownership & permissions for / trash. And then restore ownership & permissions. Not sure correct way, but worked. Sudo did not seem to give me enough.

---

### Post by bogoliubov on 2018-05-03
But when I run "du", shouldn't the root folder be included as well?

Also:
```
christian@x220:/$ sudo du -sh root/
28K	root/

```

---

### Post by rsteinmetz70112 on 2018-05-03
Have you tried running fsck on it?

---

### Post by bogoliubov on 2018-05-03
Hmm, no I haven't. But it is a BTRFS partition; could that have anything to do with my issue?

---

### Post by oldfred on 2018-05-03
Do not know about BTRFS, but you cannot use fsck as that is only for the ext2, ext3 & ext4 family of formats. You have to use BTRFS tools to repair it, if that is what is needed.

---

### Post by rsteinmetz70112 on 2018-05-04
> **oldfred said:**
> Do not know about BTRFS, but you cannot use fsck as that is only for the ext2, ext3 & ext4 family of formats. You have to use BTRFS tools to repair it, if that is what is needed.

Fsck also works with at least some other filesystems by calling their equivalent programs. I know reiserfs works like this. I have not used BTRFS so I can't say for sure.

---

### Post by Holger_Gehrke on 2018-05-04
I think this [FAQ entry]("https://btrfs.wiki.kernel.org/index.php/FAQ#How_much_free_space_do_I_have.3F") might help you.

Holger

---

### Post by bogoliubov on 2018-05-04
Thanks, but it seems that it may be something else anyway. I will check the smart status of the disk.

---

### Post by bogoliubov on 2018-05-04
Nope, the SMART status seems OK. So I can't figure out what it is. I will probably have to reinstall to see if that will solve the problem.

---

### Post by pqwoerituytrueiwoq on 2018-05-04
It looks like it is your /home folder eating most of your space
as for the data you do not see try using sudo, you do not have read access to everything (this will only check the most common places to get lots of data)
```
sudo du -sh /{boot,var,home}
82M    /boot
1.7G    /var
256G    /home
```
Old kernel images will fill /boot up eventually
A panicking program can fill up /var/log
and /home can be filled up with your data check your downloads and trash

You may want to give [baobab]("apt:bobab") a try

---

### Post by bogoliubov on 2018-05-05
Hi. No this is not the issue. The issue is that the root ( / ) partition is too full for upgrading according to df, BUT there all the files together on / do not add up to the total reported by df.

```

christian@x220:/$ df -h
Filsystem      Storlek Använt Ledigt Anv% Monterat på
/dev/sda1          23G    17G   4,9G  78% /
/dev/sda6         272G   192G    81G  71% /home

```

```

christian@x220:/$ sudo du -h --max-depth=1 
192G	./home
18M	./etc
0	./media
526M	./var
15M	./bin
133M	./boot
0	./dev
720M	./lib
4,0K	./lib64
0	./mnt
0	./opt
0	./proc
28K	./root
1,5M	./run
14M	./sbin
4,0K	./snap
0	./srv
0	./sys
6,3M	./tmp
6,2G	./usr
0	./cdrom
199G	.

```
So totally there is 199GB used, out of which 192 is /home. This means that according to du, / uses 7 GB but df reports 17GB. So there are about 10 GB used that can't be found.
I've never used such a large / partition before, but I also never had any issues with it becoming so full. Something is wrong, but I can't figure out what it is.

---

### Post by oldfred on 2018-05-05
Did you look in ./root ?
That is not normally accessible & trash may be in it.
I have had issues even seeing it with sudo.

fred@Xenial_z97:~$ sudo ls ./root
ls: cannot access './root': No such file or directory

---

### Post by VMC on 2018-05-05
```
$ sudo ls -a /root
.  ..  .bash_history  .bashrc  .cache  .profile
```

---

### Post by #&amp;thj^% on 2018-05-05
Along with VMC code.
```
cd /root && sudo ls -al
total 104
drwx------ 12 me   me   4096 Mar 18 13:33 .
drwxr-xr-x 17 root root 4096 Mar 12 11:27 ..
-rwxr-xr-x  1 me   me    787 Mar  1 10:51 .automated_script.sh
-rw-r--r--  1 root root  154 Mar  1 05:41 .bash_profile
-rw-r--r--  1 root root 1553 Mar  1 05:41 .bashrc
drwx------  4 root root 4096 Mar 12 11:43 .cache
drwxr-xr-x 17 root root 4096 Mar 17 13:59 .config
drwx------  3 root root 4096 Mar 12 11:33 .dbus
-rw-r--r--  1 root root 8504 Mar  1 05:41 .face
drwxr-xr-x  3 root root 4096 Mar 12 11:22 .gimp-2.8
drwx------  3 root root 4096 Mar  1 11:01 .gnupg
dr-x------  2 root root    0 May  5 07:32 .gvfs
-rw-r--r--  1 me   me   9013 Mar  1 11:12 install.txt
drwxr-xr-x  3 root root 4096 Mar 12 11:22 .local
drwxr-xr-x  3 root root 4096 Mar 12 11:22 .mozilla
drwxr-xr-x  3 root root 4096 Mar 12 11:22 .nano
-rw-r--r--  1 root root  173 Mar  1 05:41 .nanorc
-rw-r--r--  1 root root  162 Mar  1 05:41 .pam_environment
drwxr-xr-x  2 root root 4096 Mar 12 11:22 .quodlibet
-rw-r--r--  1 root root  215 Mar 18 13:33 .wget-hsts
-rw-r--r--  1 root root   96 Mar  1 05:41 .xinitrc
-rw-r--r--  1 root root  132 Mar  1 05:41 .Xresources
-rw-r--r--  1 me   me     23 Mar  1 10:51 .zlogin


```
Admittedly not the best for size though.
EDIT: Ha now I remember for size:
```
sudo du -hs /root
[sudo] password for me: 
1.2M	/root

```

---

### Post by bogoliubov on 2018-05-05
```
christian@x220:/$ sudo du -sh /root
[sudo] lösenord för christian: 
28K	/root

```

---

### Post by deadflowr on 2018-05-05
From arch wiki on using df and btrfs partitions:
[https://wiki.archlinux.org/index.php/Btrfs#Displaying_used.2Ffree_space]("https://wiki.archlinux.org/index.php/Btrfs#Displaying_used.2Ffree_space")

---

### Post by bogoliubov on 2018-05-06
Thanks, but none of the suggestions made any difference larger than some megabytes. I will try to reinstall.

---

