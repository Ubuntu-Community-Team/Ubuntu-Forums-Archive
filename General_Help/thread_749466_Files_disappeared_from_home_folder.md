---
title: "Files disappeared from home folder"
date: 2008-04-08
forum: General Help
---

### Post by scorziello on 2008-04-08
I was trying to copy a DVD to my hard drive when  got an error from k9copy the the directory that I was trying to copy to no longer existed. I had just finished copying a different DVD to the same file. I have looked in Lost and Found and also looked in .Trash of my home directory but with no luck. Any help would be greatly appreciated. All the other folders which are usually in the home folder by default have also gone missing.

---

### Post by tamoneya on 2008-04-08
is your /home a separate partition?  It may have just gotten unmounted.  Anyways post the output of```
ls -la ~
```

---

### Post by scorziello on 2008-04-08
Here is the output of ls -la ~
> enzo@ghost-systems:~$ ls -la /home/enzo
total 220
drwxr-xr-x 47 enzo enzo  4096 2008-04-08 14:14 .
drwxr-xr-x  4 root root  4096 2008-01-12 17:21 ..
drwx------  5 enzo enzo  4096 2008-01-21 20:51 .adobe
drwxr-xr-x  2 enzo root  4096 2008-01-12 19:13 .automatix
drwxr-xr-x  3 enzo enzo  4096 2008-01-12 15:28 .cache
drwxr-xr-x  8 enzo enzo  4096 2008-04-08 13:32 .config
drwx------  3 enzo enzo  4096 2008-02-14 16:22 .dbus
-rw-------  1 enzo enzo    28 2008-04-08 14:14 .dmrc
drwxr-xr-x  5 enzo enzo  4096 2008-04-08 12:58 .dvdcss
drwx------  2 enzo games 4096 2008-01-21 21:33 .emilia
-rw-------  1 enzo enzo    16 2008-04-08 14:14 .esd_auth
drwxr-xr-x  8 enzo enzo  4096 2008-04-08 14:14 .evolution
drwxr-xr-x  6 enzo enzo  4096 2008-04-08 12:53 .exaile
lrwxrwxrwx  1 enzo enzo    26 2008-01-12 15:22 Examples -> /usr/share/example-content
drwxr-xr-x  2 enzo enzo  4096 2008-01-12 17:50 .fontconfig
drwx------  4 enzo enzo  4096 2008-04-08 14:14 .gconf
drwx------  2 enzo enzo  4096 2008-04-08 14:14 .gconfd
drwxr-xr-x  4 enzo enzo  4096 2008-01-12 17:56 .gnome
drwx------ 16 enzo enzo  4096 2008-04-08 13:33 .gnome2
drwx------  2 enzo enzo  4096 2008-01-12 15:28 .gnome2_private
drwxr-xr-x  2 enzo enzo  4096 2008-01-12 19:52 .gstreamer-0.10
-rw-r--r--  1 enzo enzo    27 2008-04-08 14:14 .gtk-bookmarks
-rw-r--r--  1 enzo enzo    86 2008-04-08 14:14 .gtkrc-1.2-gnome2
-rw-------  1 enzo enzo   173 2008-04-08 14:14 .ICEauthority
drwxr-xr-x  2 enzo enzo  4096 2008-01-12 17:45 .icons
drwx------  3 enzo enzo  4096 2008-03-31 22:47 .kde
drwx------  3 enzo enzo  4096 2008-02-12 18:21 .keytouch2
drwx------  2 enzo enzo  4096 2008-01-21 21:35 .lincity
drwxr-xr-x  3 enzo enzo  4096 2008-01-12 15:28 .local
drwx------  3 enzo enzo  4096 2008-01-12 17:56 .loki
drwxr-xr-x  3 enzo enzo  4096 2008-04-01 17:28 .lyrics
drwx------  3 enzo enzo  4096 2008-01-12 17:12 .macromedia
drwxr-xr-x  3 enzo enzo  4096 2008-03-31 22:57 .mcop
drwx------  3 enzo enzo  4096 2008-01-12 15:28 .metacity
drwx------  3 enzo enzo  4096 2008-01-12 15:55 .mozilla
drwxr-xr-x  3 enzo enzo  4096 2008-01-24 05:22 .nautilus
drwx------  3 enzo enzo  4096 2008-04-07 20:35 .openoffice.org2
drwxr-xr-x  3 enzo enzo  4096 2008-04-08 13:31 picasa
drwxr-xr-x  4 enzo enzo  4096 2008-01-12 18:00 .picasa
drwxr-xr-x  3 enzo enzo  4096 2008-01-13 22:39 Pictures
drwx------  4 enzo enzo  4096 2008-04-08 14:14 .purple
drwxr-xr-x  2 enzo enzo  4096 2008-03-31 22:47 .qt
drwx------  3 enzo enzo  4096 2008-01-23 05:44 .scim
drwxr-xr-x  3 enzo enzo  4096 2008-01-24 04:51 .sok
drwxr-xr-x  2 enzo enzo  4096 2008-01-12 17:45 .themes
drwx------  5 enzo enzo  4096 2008-03-31 15:44 .thumbnails
drwx------  5 enzo enzo  4096 2008-01-31 17:27 .Trash
drwxr-xr-x  2 enzo enzo  4096 2008-01-12 15:28 .update-manager-core
drwx------  2 enzo enzo  4096 2008-01-12 16:00 .update-notifier
drwxr-xr-x  3 enzo enzo  4096 2008-04-07 20:45 .vlc
drwx------  2 enzo enzo  4096 2008-01-12 17:56 .w3m
drwxr-xr-x  2 enzo enzo  4096 2008-01-24 06:10 .wapi
-rw-------  1 enzo enzo   124 2008-04-08 14:14 .Xauthority
drwxr-xr-x  2 enzo enzo  4096 2008-03-31 22:49 .xine
-rw-r--r--  1 enzo enzo  5490 2008-04-08 14:14 .xsession-errors

---

### Post by tamoneya on 2008-04-08
Oh i thought you were saying you were trying to copy the files into your home directory and that your home directory was now empty.  What directory are you trying to copy to and is this directory part of a separate partition from your root partition.  If you dont know what I mean by this post the contents of /etc/fstab

---

### Post by unutbu on 2008-04-08
If you know the name of the file or directory you are looking for (or even a piece of the name) you could do this:

```
sudo updatedb
locate file-or-directory
```

---

### Post by scorziello on 2008-04-08
I don't think you understand what I am talking about. When I logon with my user name all my entire home directory seems to have just vanished so much so that even my firefox settings that I had saved are no longer there. It is almost like it reset a lot of things but all of my programs are still there, and my desktop settings are still the same, AWN is still in place and so are all my icons but when I go to look in /home/enzo/Music or /Movies those files are not there. The only files in my home folder are examples, picasa, and pictures and they are all empty. Also showing hidden files does not help, my hidden files are there but not the ones I am missing.

---

### Post by unutbu on 2008-04-08
This sounds like a mounting problem.
Please post the output to

```
cat /etc/fstab
df -h
```

---

### Post by scorziello on 2008-04-08
The other home directory on the drive is fine here is the output:
enzo@ghost-systems:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9b7547a5-0dc5-4ebb-ac2d-30f6a30337ca /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=998251a0-f559-4c8f-a569-af8546c439c9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
enzo@ghost-systems:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             181G  4.4G  168G   3% /
varrun                474M   92K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
udev                  474M   84K  474M   1% /dev
devshm                474M     0  474M   0% /dev/shm
lrm                   474M   34M  440M   8% /lib/modules/2.6.22-14-generic/volatile
/dev/sdf1              56G   15G   42G  27% /media/disk
/dev/hdc              7.4G  7.4G     0 100% /media/cdrom0

---

### Post by unutbu on 2008-04-08
Hm. Would you please also post

```
sudo fdisk -l
```

---

### Post by scorziello on 2008-04-08
Here you go, just want to say thanks in advance. This is the first time I have been stumped like this.

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23968   192522928+  83  Linux
/dev/sda2           23969       24321     2835472+   5  Extended
/dev/sda5           23969       24321     2835441   82  Linux swap / Solaris

Disk /dev/sdf: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6be40a0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        7296    58605088+   b  W95 FAT32

---

### Post by unutbu on 2008-04-09
scorziello, I'm really sorry but I'm stumped too.

I take it from your /etc/fstab that your /home directory was not on a separate partition. If that's the case then yours is not a mounting problem.

I take it when you say 'the other home directory' is fine you mean /dev/sdf1 which is mounted at /media/disk?

If all your drives and partitions are accounted for and your home partition looks borked, then I'm afraid your home partition might be well and truly borked.

What's strange is that you still have files in your home directory, it's just that they are a few months old (mostly from January) and you have no files/dirs other than dot files/dirs (other than Examples). 

I hope someone else here can help you. :(

---

### Post by scorziello on 2008-04-09
Hey thanks for your help. I was hoping that was not the case but that is what it seemed to me as well. I will have to create a new userid and go from there.

---

### Post by Tomatz on 2008-04-09
Did you run any commands from a forum/wiki with the command **rm** in it

---

### Post by scorziello on 2008-04-09
No I do no better than that, I do appreciate the concern.

---

### Post by Tomatz on 2008-04-09
> **scorziello said:**
> No I do no better than that, I do appreciate the concern.

Cool ;)

Just wanted to cover all bases.

---

### Post by lonewolf_timberwolf on 2008-04-23
I just had this exact thing happen to me! I backed up a dvd using k9copy and after I closed the program, all of my desktop icons were gone, and so is everything in my home folder!

---

### Post by danwood76 on 2008-04-23
k9copy bug?

---

### Post by lonewolf_timberwolf on 2008-04-23
I hope not. Surely its not THAT big of a bug where it wipes my files. That'd be a heck of a changelog "Fixed: No longer wipes files"

I figure my files have to be here somewhere. I'm just too newb to find them. However, I do believe I set my home folder to a separate partition. But when go into a terminal and check the two partitions I have (a 9.5 GB and a 70 GB) I get a home folder for each. Yet when I check both folders, they're exactly the same. I created one blank file in one, and I can see it in another. Is my home directory pointing to somewhere new?

---

