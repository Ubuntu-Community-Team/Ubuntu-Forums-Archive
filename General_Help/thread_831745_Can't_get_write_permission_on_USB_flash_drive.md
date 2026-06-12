---
title: "Can't get write permission on USB flash drive"
date: 2008-06-17
forum: General Help
---

### Post by Shampyon on 2008-06-17
I have a thumb drive full of portable apps that I use to carry my web design work around to Windows computers. I mainly use it on a Win2K computer at work.

I tried to cut-n-paste the contents of the drive to my desktop so I could put some videos on it and plug it into my DVD player (big screen TV and a comfy lounge beats 17" CRT and a single bed). The operation fails, saying I don't have permissions.

When I check the properties of the disk, it says

OWNER: Shampyon *(not my real account name)*
GROUP: root
I try changing the OWNER/GROUP as Shampyon to SHAMPYON/USERS, but it says I don't have the right permissions. I open nautilus as ROOT, I STILL don't have permissions. I try from terminal: still won't work.

I can copy the files to my hard drive easily enough, but I just don't have cut and rewrite permissions on the thumb drive. I'm having to reformat the drive just to use it at home, and when I copy my work files back I know the problem will start all over again.

---

### Post by dnairb on 2008-06-20
I have the exact problem, with 2 USB sticks.

Deleting / re-creating partitions with gparted doesn't fix the problem.

Even using **sudo su** and performing **chown** commands doesn't work.

I'm left with 2 USB drives, which I own, but the group is root so I can't do anything with them (except for deleting / recreating partitions)

This seemed to have happened after upgrading the kernel to -19. Has anybody else had this issue?

---

### Post by bbyrd on 2008-06-21
I have encountered a similar problem since the -19 kernel. I have a 320GB external hard drive (with 4 ntfs partitions)which is used to share/store/backup data from a number of different machines/locations (linux, xp & vista). 

I have just found that I no longer have write permission. Under permissions the owner is listed as root, despite the fact that the drive was automounted after log-in (and should be owned by user - AFAIK).

I should note that I recently changed from Ubuntu (Gnome) to Xubuntu (Xfce) - might this be something to do with it? Do Ubuntu and Xubuntu handle automounts differently?

Any help appreciated!!
- your friendly local Linux noob.

---

### Post by davidshere on 2008-09-05
Same problem with my Sandisk Cruzer (working normally for the past six months), but worse:  I don't have read or write permissions.  I was using the drive normally:

1.  Deleted file
2.  Unmounted drive
3.  Waited until it said it was ok to remove
4.  Removed drive
5.  Waited 5-10 seconds
6.  Put drive back in

Ubuntu says I don't have permissions necessary to view contents.  I tried this, and as you can see, it didn't work:

```
david@raptor:/media$ sudo chmod -R 777 disk
david@raptor:/media$ ls -lash
total 32K
4.0K drwxr-xr-x  5 root root 4.0K 2008-09-05 09:55 .
4.0K drwxr-xr-x 22 root root 4.0K 2008-06-16 15:54 ..
   0 lrwxrwxrwx  1 root root    6 2007-10-22 10:27 cdrom -> cdrom0
4.0K drwxr-xr-x  2 root root 4.0K 2007-10-22 10:27 cdrom0
4.0K drwxr-xr-x  2 root root 4.0K 2007-10-22 10:27 cdrom1
 12K drwx------  9 root root  12K 1969-12-31 19:00 disk
4.0K -rw-r--r--  1 root root  104 2008-09-05 09:55 .hal-mtab
   0 -rw-------  1 root root    0 2008-09-05 09:49 .hal-mtab-lock
david@raptor:/media$ 

```

EDIT:  Rebooted, works fine.

---

### Post by physeetcosmo on 2009-02-18
Nix peeps,

I am having a similar issue which occurred after I used unetbootin to place a liveCD .iso on my SDCard. As you can see:
```
dustin@SuperNIX:~/Documents$ ls -lash
total 2.2M
4.0K drwxr-xr-x  9 dustin dustin 4.0K 2009-02-17 23:15 .
4.0K drwxr-xr-x 54 dustin dustin 4.0K 2009-02-18 08:38 ..
504K -rw-r--r--  1 dustin dustin 499K 2009-02-10 11:58 Context Switch Pt1.pdf
1.1M -rw-r--r--  1 dustin dustin 1.1M 2009-02-10 11:59 Context Switch Pt2.pdf
544K -rw-r--r--  1 dustin dustin 538K 2009-02-10 12:00 Context Switch Pt3.pdf
[COLOR="Red"] 16K -r--r--r--  1 root   root    13K 2009-02-17 23:11 extlinux.sys[/COLOR]
 16K drwx------  2 root   root    16K 2009-02-10 11:42 lost+found
4.0K drwxr-xr-x  5 dustin dustin 4.0K 2009-02-10 11:46 Metro
4.0K drwxr-xr-x  4 dustin dustin 4.0K 2009-02-10 11:46 Pictures
 12K -rw-r--r--  1 dustin dustin 9.3K 2009-02-17 08:26 publickey.txt
4.0K drwx------  4 root   root   4.0K 2009-02-17 23:15 .Trash-0
4.0K drwxr-xr-x  4 dustin dustin 4.0K 2009-02-13 16:58 .Trash-1000
4.0K drwxr-xr-x  5 dustin dustin 4.0K 2009-02-10 11:46 Utilities
4.0K drwxr-xr-x  4 dustin dustin 4.0K 2009-02-10 11:45 White Papers

```
I have a file that has root ownership and group standing (file: extlinux.sys) of which I am trying to remove. I have attempted:
```
$ chmod a=rwx
$ chown dustin
$ chgrp dustin
```
but these keep giving me an error of:```
dustin@SuperNIX:~/Documents$ sudo chmod a=rwx ./extlinux.sys
chmod: changing permissions of `./extlinux.sys': Operation not permitted

```
I have also tried changing permissions through nautilus, using:
```
$ gksudo nautilus /home/dustin/Documents
```
which is where my SDCard is mounted. Why are the permission stuck? Does this have to do with the 'sticky bit'?
My SDCard is formatted with ext3 as seen from:```
dustin@SuperNIX:~/Documents$ df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3    7.4G  2.8G  4.3G  40% /
tmpfs        tmpfs   1009M     0 1009M   0% /lib/init/rw
varrun       tmpfs   1009M  112K 1008M   1% /var/run
varlock      tmpfs   1009M     0 1009M   0% /var/lock
udev         tmpfs   1009M  2.8M 1006M   1% /dev
tmpfs        tmpfs   1009M  104K 1008M   1% /dev/shm
/dev/sdb5     ext3     30G  5.3G   23G  19% /home
[color="red"]/dev/sdc1     ext3    966M   40M  877M   5% /home/dustin/Documents[/color]
/dev/sdd1     vfat    948M   52M  897M   6% /media/DSL_

```
Thanks in advance! I will try and solve another way.

---

### Post by djzoid on 2010-01-07
hey, i have a sandisk cruzer plugged into my eee 900 ubuntu hardy, according to this post [http://ubuntuforums.org/archive/index.php/t-1091230.html](http://ubuntuforums.org/archive/index.php/t-1091230.html) by "nothingspecial" it's likely that an immutable flag is set so you cant do anything to the file until you remove it:

"If it's ext2, it may be that you have the immutable flag set on the file, or the directory containing it.

try using
```
lsattr extlinux.sys
 lsattr -d /path
```where path is again the path to the directory containing extlinux.sys
If either of those outputs something like:
----i------------- extlinux.sys
then you have an immutable flag set, which you can remove using (eg)
```
sudo chattr -i extlinux.sys
```"

This may be helpful to those wishing to clear their usb drive after using unetbootin bootlader.

hope this is useful.

---

