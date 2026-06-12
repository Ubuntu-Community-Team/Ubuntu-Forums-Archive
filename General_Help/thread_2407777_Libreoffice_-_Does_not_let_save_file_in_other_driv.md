---
title: "Libreoffice - Does not let save file in other drives."
date: 2018-12-09
forum: General Help
---

### Post by vigisbig786 on 2018-12-09
Hi,

I am new to Ubuntu, so please be easy on me.

I recently installed Ubuntu and the new partitions were made. I am now the owner of all partitions. I used 'chown' command to do this. And I can now create new folders and save files in these drives. However, when I try to save files in libreoffice, it does not let me save in other drives. The drives are not show while I can see them from file manager. Also, if I paste the file in these locations (other drives) (after saving it on desktop), libreoffice shows an error, saying file does not exist when I try to open them.

I also tried WPS office, ONLY OFFICE etc. they also don't show other drives while saving files. I wonder what's wrong.

I cannot solve the problem. Any help will be appreciated, Please warn me if it would make the problem worse (Like make system unbootable). I have already installed ubuntu atleast 5 times due to mistakes.

Thanks.
Pankaj

---

### Post by corradoventu on 2018-12-09
If the partitions are empty you may try to format them from your user.
do you see the partitions in GPARTED?
Libreoffice is a SNAP app?
Please post the output from
```
snap list
```

---

### Post by TheFu on 2018-12-09
Are you certain this is a program problem and not just file permissions?
Please post the cmd and output from
```
ls -l /path/to/the/files
df -Th
```

This will show the owner, group and permissions. The df command will show what is mounted and the file systems used.

---

### Post by ajgreeny on 2018-12-09
And have you made those partitions mount at boot by adding a line to /etc/fstab file?

Show us the output of ```
sudo blkid -c /dev/null
sudo fdisk -l
```
Please use **Code-Tags** for terminal output to show that text in a more readable format, the same as it is in the terminal, not as plain text. See my signature below for a **How-to**

---

### Post by vigisbig786 on 2018-12-12
> **corradoventu said:**
> If the partitions are empty you may try to format them from your user.
do you see the partitions in GPARTED?
Libreoffice is a SNAP app?
Please post the output from
```
snap list
```

Yes, I do see them in Gparted. I am not sure if formatting will solve the problem. Since when partition was created, I did format them. 

Yes, Libreoffice was a snap app. I uninstalled it at the moment. Here's the output I get. At the moment I have installed only librewriter (word) and not the complete suite that has other programs like excel etc. it lets me save file in any of the disk without any issue. However, it's nice to have complete suite if my problems solves

==============
```

 pankaj@pankaj-Vostro1510:~$ snap listName                  Version         Rev   Tracking  Publisher   Notes
canonical-livepatch   8.0.6           50    stable    canonical*  -
core                  16-2.36.2       6034  stable    canonical*  core
gnome-3-26-1604       3.26.0          74    stable/…  canonical*  -
gnome-calculator      3.30.1          260   stable/…  canonical*  -
gnome-characters      3.30.0          139   stable/…  canonical*  -
gnome-logs            3.30.0          45    stable/…  canonical*  -
gnome-system-monitor  3.30.0          57    stable/…  canonical*  -
gtk-common-themes     0.1-4-g88bc1b2  818   stable/…  canonical*  -
vlc                   3.0.4           555   stable    videolan*   -

```

==============

Thanks for the help

---

### Post by vigisbig786 on 2018-12-12
> **TheFu said:**
> Are you certain this is a program problem and not just file permissions?
Please post the cmd and output from
```
ls -l /path/to/the/files
df -Th
```

This will show the owner, group and permissions. The df command will show what is mounted and the file systems used.

I am not sure what do you mean by permissions. I can create folders and save files in those drives otherwise. 

Here's my output.

```


pankaj@pankaj-Vostro1510:~$ ls -l /path/to/the/files
ls: cannot access '/path/to/the/files': No such file or directory
pankaj@pankaj-Vostro1510:~$ sudo ls -l /path/to/the/files
[sudo] password for pankaj: 
ls: cannot access '/path/to/the/files': No such file or directory



pankaj@pankaj-Vostro1510:~$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     395M  1.9M  393M   1% /run
/dev/sda1      ext4       42G  8.7G   32G  22% /
tmpfs          tmpfs     2.0G   27M  1.9G   2% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/loop1     squashfs   13M   13M     0 100% /snap/gnome-characters/103
/dev/loop3     squashfs   35M   35M     0 100% /snap/gtk-common-themes/319
/dev/loop5     squashfs  5.0M  5.0M     0 100% /snap/canonical-livepatch/50
/dev/loop6     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/51
/dev/loop7     squashfs  2.4M  2.4M     0 100% /snap/gnome-calculator/180
/dev/loop9     squashfs   87M   87M     0 100% /snap/core/4917
/dev/loop0     squashfs  2.3M  2.3M     0 100% /snap/gnome-calculator/260
/dev/loop11    squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/57
/dev/loop4     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/74
/dev/loop8     squashfs   15M   15M     0 100% /snap/gnome-logs/45
/dev/loop12    squashfs   35M   35M     0 100% /snap/gtk-common-themes/818
/dev/loop10    squashfs   90M   90M     0 100% /snap/core/6034
/dev/loop13    squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop2     squashfs  196M  196M     0 100% /snap/vlc/555
/dev/loop14    squashfs   15M   15M     0 100% /snap/gnome-logs/37
/dev/loop15    squashfs   89M   89M     0 100% /snap/core/5897
/dev/loop16    squashfs   13M   13M     0 100% /snap/gnome-characters/139
/dev/sda6      ext4       93G   61M   88G   1% /d
/dev/sda7      ext4       93G   61M   88G   1% /e
tmpfs          tmpfs     395M   16K  395M   1% /run/user/121
tmpfs          tmpfs     395M   32K  395M   1% /run/user/1000




```

Thanks for the help

---

### Post by vigisbig786 on 2018-12-12
> **ajgreeny said:**
> And have you made those partitions mount at boot by adding a line to /etc/fstab file?

Show us the output of ```
sudo blkid -c /dev/null
sudo fdisk -l
```
Please use **Code-Tags** for terminal output to show that text in a more readable format, the same as it is in the terminal, not as plain text. See my signature below for a **How-to**

I am sorry, I don't understand what you mean. Here's the output that you asked.

```


pankaj@pankaj-Vostro1510:~$ sudo blkid -c /dev/null
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="cb3f2338-0c2a-4934-bf84-b8ad5d5673de" TYPE="ext4" PARTUUID="e8c4cb87-01"
/dev/sda5: UUID="f2c5236d-9834-430a-ac6b-ecf5b83859d5" TYPE="swap" PARTUUID="e8c4cb87-05"
/dev/sda6: UUID="ff9f22b5-bf2a-4fe1-83f9-0a5812d0ab42" TYPE="ext4" PARTUUID="e8c4cb87-06"
/dev/sda7: UUID="532e9133-0304-46f5-a8d4-03cd1ec14fd4" TYPE="ext4" PARTUUID="e8c4cb87-07"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"










pankaj@pankaj-Vostro1510:~$ sudo fdisk -l
[sudo] password for pankaj: 
Disk /dev/loop0: 2.3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 195.2 MiB, 204644352 bytes, 399696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 34.7 MiB, 36323328 bytes, 70944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 140.7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 4.9 MiB, 5148672 bytes, 10056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 3.7 MiB, 3887104 bytes, 7592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop7: 2.3 MiB, 2433024 bytes, 4752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes








Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe8c4cb87


Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048  89999359  89997312 42.9G 83 Linux
/dev/sda2        90001406 488396799 398395394  190G  5 Extended
/dev/sda5        90001408  93999103   3997696  1.9G 82 Linux swap / Solaris
/dev/sda6        94001152 291198975 197197824   94G 83 Linux
/dev/sda7       291201024 488396799 197195776   94G 83 Linux




Disk /dev/loop8: 14.5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop9: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop10: 89.5 MiB, 93818880 bytes, 183240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop11: 3.7 MiB, 3878912 bytes, 7576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop12: 34.6 MiB, 36216832 bytes, 70736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop13: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop14: 14.5 MiB, 15196160 bytes, 29680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop15: 88.2 MiB, 92483584 bytes, 180632 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop16: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes






```

Thanks

---

### Post by yancek on 2018-12-12
Your df-h output shows that you have partitions sda6 and sda7 mounted at /d and e/ respectively.  The ls -l command shows the owner:group and who has read, write and execute permissions.  The command posted earlier was just an example and you need to use the actual path which in your case should be:

> ls -l /d
ls -l /e

---

### Post by TheFu on 2018-12-12
Thanks Yancek. That information will be helpful.

The fstab file contents are needed still as well. Without that, we can't see how the extra storage is mounted.  Another option to see the same information would be to show the output from **mount** for the partitions involved.

The **df -Th** output.```

/dev/sda6      ext4       93G   61M   88G   1% /d
/dev/sda7      ext4       93G   61M   88G   1% /e
```

This tells us that we don't need to worry about non-native Linux file systems like NTFS or FAT32, which are troublesome for managing permissions.  But we still need the **ls -l **output to know if permissions are any issue. 

At this point, I have 2 guesses for the issue remaining. Snaps have been removed and NTFS permissions have been removed, so we are making progress.

a) Not using a "real" mount
b) Unix file permissions

I'm leaning to wards file permissions since hardly any data is stored on those partitions. It is puzzling the claim that other programs aren't having issues writing data to the storage.  Seeing the permissions for those files will help greatly.

---

### Post by vigisbig786 on 2018-12-12
> **yancek said:**
> Your df-h output shows that you have partitions sda6 and sda7 mounted at /d and e/ respectively.  The ls -l command shows the owner:group and who has read, write and execute permissions.  The command posted earlier was just an example and you need to use the actual path which in your case should be:

```

pankaj@pankaj-Vostro1510:~$ ls -l /d
total 16
drwx------ 2 pankaj pankaj 16384 Dec  9 13:29 lost+found
pankaj@pankaj-Vostro1510:~$ ls -l /e
total 20
drwxrwxr-x 2 pankaj pankaj  4096 Dec 12 22:07 IGNOU
drwx------ 2 pankaj pankaj 16384 Dec  9 13:29 lost+found
pankaj@pankaj-Vostro1510:~$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     395M  1.9M  393M   1% /run
/dev/sda1      ext4       42G  8.9G   31G  23% /
tmpfs          tmpfs     2.0G   46M  1.9G   3% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/loop0     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop2     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/57
/dev/loop13    squashfs  2.3M  2.3M     0 100% /snap/gnome-calculator/260
/dev/loop3     squashfs   13M   13M     0 100% /snap/gnome-characters/139
/dev/loop1     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/74
/dev/loop4     squashfs   13M   13M     0 100% /snap/gnome-characters/103
/dev/loop11    squashfs   15M   15M     0 100% /snap/gnome-logs/37
/dev/loop8     squashfs   89M   89M     0 100% /snap/core/5897
/dev/loop5     squashfs   35M   35M     0 100% /snap/gtk-common-themes/319
/dev/loop7     squashfs   35M   35M     0 100% /snap/gtk-common-themes/818
/dev/loop6     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/51
/dev/loop14    squashfs  2.4M  2.4M     0 100% /snap/gnome-calculator/180
/dev/loop9     squashfs  5.0M  5.0M     0 100% /snap/canonical-livepatch/50
/dev/loop10    squashfs   87M   87M     0 100% /snap/core/4917
/dev/loop12    squashfs   15M   15M     0 100% /snap/gnome-logs/45
/dev/loop15    squashfs   90M   90M     0 100% /snap/core/6034
/dev/sda6      ext4       93G   61M   88G   1% /d
/dev/sda7      ext4       93G   61M   88G   1% /e
tmpfs          tmpfs     395M   16K  395M   1% /run/user/121
tmpfs          tmpfs     395M   52K  395M   1% /run/user/1000




```

Thanks for the help again! :-)

---

### Post by corradoventu on 2018-12-13
You can install libreoffice in deb format from Ubuntu Software

---

### Post by vigisbig786 on 2018-12-13
> **corradoventu said:**
> You can install libreoffice in deb format from Ubuntu Software

That's how I did two times. Same result. Anyway, thanks for the help. I read many people have faced the same problem. Looks like something wrong with Libreoffice build or something like that, not a permission issue but perhaps the default file / attributes that are set in Libre office.

Regards,
Pankaj

---

### Post by TheFu on 2018-12-13
So ... no **mount** output, as requested?  Need to see the mount options while the storage is available.

---

### Post by vigisbig786 on 2018-12-15
> **TheFu said:**
> So ... no **mount** output, as requested?  Need to see the mount options while the storage is available.

How do I do that?

---

### Post by deadflowr on 2018-12-15
> **vigisbig786 said:**
> How do I do that?

Just post the output of
```
mount | grep /dev/sd
```
the mount command will show info about the mounted partitions and the grep will cut it down to only show the disks.
(And not show any of those pesky snap loop devices or tmpfs  and other virtual file systems)

---

### Post by vigisbig786 on 2018-12-15
> **deadflowr said:**
> Just post the output of
```
mount | grep /dev/sd
```
the mount command will show info about the mounted partitions and the grep will cut it down to only show the disks.
(And not show any of those pesky snap loop devices or tmpfs  and other virtual file systems)

Ok. Is this what is required? Thanks for the help everyone.

```


pankaj@pankaj-Vostro1510:~$ mount | grep /dev/sd
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda7 on /e type ext4 (rw,relatime,data=ordered)
/dev/sda6 on /d type ext4 (rw,relatime,data=ordered)



```

---

### Post by ubname on 2018-12-15
Hi vigisbig,

I see that you are referring to "other drives" but you have in fact two extra partition in "sda" (which is your only actual drive).
I think you made an error configuring in that way your system; let me also assure you that libreoffice can write to other drives,
I have indeed two actual drives in my system ("sda" and "sdb") and there are no problems writing and reading with libreoffice.

If you have one drive, the best you can do is reinstall and let the system manage your filesystem structure, there is no need
to have partition that point to /e and /d; I understand that it may seem more familiar to you if you are more experienced with windows
but it is useless and problematic (as you already noticed)

When you install ubuntu all your personal and work files will be in your "/home" directory which will have your user name ( i.e /home/vigisbig )

HTH.

---

### Post by vigisbig786 on 2018-12-17
> **ubname said:**
> Hi vigisbig,

I see that you are referring to "other drives" but you have in fact two extra partition in "sda" (which is your only actual drive).
I think you made an error configuring in that way your system; let me also assure you that libreoffice can write to other drives,
I have indeed two actual drives in my system ("sda" and "sdb") and there are no problems writing and reading with libreoffice.

If you have one drive, the best you can do is reinstall and let the system manage your filesystem structure, there is no need
to have partition that point to /e and /d; I understand that it may seem more familiar to you if you are more experienced with windows
but it is useless and problematic (as you already noticed)

When you install ubuntu all your personal and work files will be in your "/home" directory which will have your user name ( i.e /home/vigisbig )

HTH.

Thanks for the clarification! :-)

I just want to ask if the two drives that you have are separate hard drives? I did partitions thinking that it may make my system fast. Indeed if it comes with these consequences, it's better not to do it. I was worried it may make the system slow.

Perhaps, I will make a correction next time I install. 

Thanks!

---

### Post by ubname on 2018-12-17
Yes, I have two separate physical drives, and the 2nd one is mapped to my user folder as a folder called "datadisk2" that I can use as any other folder, the fact that that folder is indeed a second disk is totally transparent to daily usage;
 The Linux file system is of course different from the windows's one, having more partitions (which may be useful for special use cases) is in general just a complication and will not make your Linux system faster or slower just more complicated.

---

