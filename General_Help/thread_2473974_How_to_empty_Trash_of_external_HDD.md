---
title: "How to empty Trash of external HDD"
date: 2022-04-20
forum: General Help
---

### Post by satimis on 2022-04-20
How to empty trash of an external hdd mounted on docking via USB

Fail to delete file on Trash on "File Manager"
Warning:```

You do not have sufficient permission delete file
...
Failed to delete the item from the trash

```
Pls see screenshot

Pls help.  Tks

Regards

---

### Post by vanadium on 2022-04-20
The trash on the USB is stored in a directory .Trash-<uid>. Somehow, ownership or permissions on some trashed files are such that you cannot delete these as normal user. You can wipe that directory as root user: it will be recreated as you delete files.

This should not happen on normal use, but could happen if you run for example graphical file managers with root permissions - don't do that.

---

### Post by ActionParsnip on 2022-04-20
You can use trash-cli to empty the trash if you like. You can prefix it with "sudo" if the file in the trash is root owned. If the file is on USB then just mount the USB and delete the file using sudo

---

### Post by satimis on 2022-04-20
Hi all,

Thanks for your advice.

I haven't done anything on the deleted data/files which include document files and software, including ISOs.  I just did house-keeping on the external HDD, deleting old files and software which I don't need them.  Deleting action went through without complaint.  But on emptying the Trash, 3 ISOs left behind.  Instead of being deleted they are triplicated.

Please refer to sceenshot-1

Remark:
Both internal and external HDDs are mounted.  They are 4TB WD HDDs, without OS installed and on ext4 format.  They are used for data storage ONLY.

Ubuntu 20.04 is running on a 1TB NVMe PCIe 3.0 SSD

Another strange thing is;
debian-11.2.0-amd64-netinst.iso
linuxmint-20.2-cinnamon-64bit-edge.iso
ubuntu-20.04.3-desktop-amd64.iso

are still there on following folder and sub-folders
PC1A_Data_20181231_20220430/1_PC1A_Data_Technical_20211231_20220430/Software_20211231_20220430/ISO/
without deleted.

Furthermore, if without mounting the external HDD, Trash is empty.

I don't know what to do?  Mount the external HDD on another PC to test it?

Regards

---

### Post by &amp;KyT$0P# on 2022-04-20
Please mount your external drive, open a Terminal at its mount point and post the output from running this command in Terminal -
```
ls -la .Trash*
```

---

### Post by vanadium on 2022-04-20
Did you try any one of the suggestions?

---

### Post by satimis on 2022-04-20
> **halogen2 said:**
> Please mount your external drive, open a Terminal at its mount point and post the output from running this command in Terminal -
```
ls -la .Trash*
```
Sorry I don't follow what is "open a Terminal at its mount point"?

On plugging the USB cable the external HDD is automatically mounted.

Performed following steps on Terminal ;
$ ls -la .Trash*```

ls: cannot access '.Trash*': No such file or directory
```

$ su -
Password: 

# ls -la .Trash*```

ls: cannot access '.Trash*': No such file or directory
```

Regards

---

### Post by #&amp;thj^% on 2022-04-20
first try this:
```
cd ~/.local/share/Trash
```
then run:
```
ls -la .Trash*
```
this may work a bit better though:
```
ls -la /home/*/.local/share/Trash
total 20
drwx------   5 me me 4096 Apr 12 12:54 .
drwx--x---+ 24 me me 4096 Apr 20 09:45 ..
drwx------   2 me me 4096 Apr 12 12:54 expunged
drwx------   2 me me 4096 Apr 12 12:54 files
drwx------   2 me me 4096 Apr 12 12:54 info

```
Apologies seen where this is on an external drive:
cd to that drive as my case shows:
```
cd /run/media/me/'My Passport'/

```
then run:
```
ls -la
```
find the Trash or Recycle bin:
```
drwxrwxrwx  1 me   me     4096 Apr 19 14:17  .
drwxr-x---+ 3 root root     60 Apr 20 10:33  ..
drwxrwxrwx  1 me   me        0 Jan 21  2021 '$RECYCLE.BIN'


```
My case I cd to 
```
cd '$RECYCLE.BIN'

```
then 
```
ls -la
total 4
drwxrwxrwx 1 me me    0 Jan 21  2021 .
drwxrwxrwx 1 me me 4096 Apr 19 14:17 ..
drwxrwxrwx 1 me me    0 Jan 21  2021 S-1-5-21-886641068-3535442022-3780765677-1001

```

---

### Post by satimis on 2022-04-20
> **ActionParsnip said:**
> You can use trash-cli to empty the trash if you like. You can prefix it with "sudo" if the file in the trash is root owned. If the file is on USB then just mount the USB and delete the file using sudo
I don't have trash-cli installed

$ apt policy trash-cli```

trash-cli:
  Installed: (none)
  Candidate: 0.17.1.14-2ubuntu1
  Version table:
     0.17.1.14-2ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe i386 Packages

```

Can I run;
$ sudo rm -rf ~/.local/share/Trash/*

instead ?

Regards

---

### Post by satimis on 2022-04-20
> **1fallen said:**
> first try this:
```
cd ~/.local/share/Trash
```
then run:
```
ls -la .Trash*
```
this may work a bit better though:
```
ls -la /home/*/.local/share/Trash
total 20
drwx------   5 me me 4096 Apr 12 12:54 .
drwx--x---+ 24 me me 4096 Apr 20 09:45 ..
drwx------   2 me me 4096 Apr 12 12:54 expunged
drwx------   2 me me 4096 Apr 12 12:54 files
drwx------   2 me me 4096 Apr 12 12:54 info

```
$ cd ~/.local/share/Trash

$ ls -la .Trash*
ls: cannot access '.Trash*': No such file or directory

$ ls -al```

total 60
drwx------  5 satimis satimis  4096 Nov 17  2019 .
drwx------ 34 satimis satimis  4096 Apr 20 22:26 ..
drwx------  2 satimis satimis  4096 Apr 20 21:13 expunged
drwx------  2 satimis satimis 20480 Apr 20 21:13 files
drwx------  2 satimis satimis 24576 Apr 20 21:13 info

```
It is empty.  The ISOs are NOT there?

Regards

---

### Post by #&amp;thj^% on 2022-04-20
I edited my first post to reflect, what I missed "external drive"

---

### Post by &amp;KyT$0P# on 2022-04-20
> **satimis said:**
> Sorry I don't follow what is "open a Terminal at its mount point"?

The mount point is the directory at which the drive is mounted.  According to your screenshots, in this case it's a folder inside /media/satimis/ with name starting with "E0C8B18". 
 So with the drive mounted, just open a Terminal and cd to this "/media/satimis/E0C8B18..." directory.  Once there, run
```
ls -la .Trash*
```

---

### Post by satimis on 2022-04-20
> **halogen2 said:**
> The mount point is the directory at which the drive is mounted.  According to your screenshots, in this case it's a folder inside /media/satimis/ with name starting with "E0C8B18". 
 So with the drive mounted, just open a Terminal and cd to this "/media/satimis/E0C8B18..." directory.  Once there, run
```
ls -la .Trash*
```
$ cd /media/satimis/E0C8B186C8B15C0A1/PC1A_Data_20181231_20220430/1_PC1A_Data_Technical_20211231_20220430/Software_20211231_20220430/ISO/

satimis@PCIeSSD1T:/media/satimis/E0C8B186C8B15C0A1/PC1A_Data_20181231_20220430/1_PC1A_Data_Technical_20211231_20220430/Software_20211231_20220430/ISO$ ls -la .Trash*```

ls: cannot access '.Trash*': No such file or directory

```

Regards

---

### Post by #&amp;thj^% on 2022-04-20
Is this really an ISO drive??? IE:"cd /media/satimis/E0C8B186C8B15C0A1/PC1A_Data_20181231_20220430/1_PC1A_Data_Technical_20211231_20220430/Software_20211231_20220430**_/ISO/"_**

---

### Post by satimis on 2022-04-20
> **1fallen said:**
> I edited my first post to reflect, what I missed "external drive"

cd /run/media/me/'My Passport'/ 

What shall I replace /media/me/'My Passport'/ ?

Thanks

Regards

---

### Post by #&amp;thj^% on 2022-04-20
Show this first:
```
df -H
```

---

### Post by satimis on 2022-04-20
> **1fallen said:**
> Show this first:
```
df -H
```
satimis@PCIeSSD1T:~$ df -H```

Filesystem                   Size  Used Avail Use% Mounted on
udev                          16G     0   16G   0% /dev
tmpfs                        3.2G  2.0M  3.2G   1% /run
/dev/mapper/ubuntu--vg-root  983G  604G  330G  65% /
tmpfs                         16G  337M   16G   3% /dev/shm
tmpfs                        5.3M  4.1k  5.3M   1% /run/lock
tmpfs                         16G     0   16G   0% /sys/fs/cgroup
/dev/loop2                    66M   66M     0 100% /snap/core20/1376
/dev/loop3                   118M  118M     0 100% /snap/core/12941
/dev/loop4                    66M   66M     0 100% /snap/core20/1405
/dev/loop6                   2.8M  2.8M     0 100% /snap/gnome-system-monitor/174
/dev/loop5                   171M  171M     0 100% /snap/gnome-3-28-1804/145
/dev/loop0                   132k  132k     0 100% /snap/bare/5
/dev/loop1                    59M   59M     0 100% /snap/core18/2284
/dev/loop7                   291M  291M     0 100% /snap/gimp/380
/dev/loop9                    59M   59M     0 100% /snap/core18/2344
/dev/loop8                   173M  173M     0 100% /snap/gnome-3-28-1804/161
/dev/nvme0n1p1               536M  5.5M  531M   2% /boot/efi
/dev/loop10                  261M  261M     0 100% /snap/gnome-3-38-2004/87
/dev/loop11                  411M  411M     0 100% /snap/gimp/383
/dev/loop13                  116M  116M     0 100% /snap/core/12834
/dev/loop12                  263k  263k     0 100% /snap/gtk2-common-themes/9
/dev/loop14                  2.8M  2.8M     0 100% /snap/gnome-system-monitor/169
/dev/loop15                   69M   69M     0 100% /snap/gtk-common-themes/1515
/dev/loop16                  263k  263k     0 100% /snap/gtk2-common-themes/13
/dev/loop17                  230M  230M     0 100% /snap/gnome-3-34-1804/77
/dev/loop18                  230M  230M     0 100% /snap/gnome-3-34-1804/72
/dev/loop19                   69M   69M     0 100% /snap/gtk-common-themes/1519
/dev/loop20                  311M  311M     0 100% /snap/vlc/2344
/dev/loop21                  261M  261M     0 100% /snap/gnome-3-38-2004/99
/dev/loop22                  274M  274M     0 100% /snap/kde-frameworks-5-core18/32
tmpfs                        3.2G   70k  3.2G   1% /run/user/1000
/dev/sdd2                    4.1T  753G  3.3T  19% /media/satimis/E0C8B186C8B15C0A1

```

---

### Post by &amp;KyT$0P# on 2022-04-20
> **satimis said:**
> $ cd /media/satimis/E0C8B186C8B15C0A1/PC1A_Data_20181231_20220430/1_PC1A_Data_Technical_20211231_20220430/Software_20211231_20220430/ISO/

Sorry, apparently I wasn't clear.  That's too many levels deep.  Please do
```
cd /media/satimis/E0C8B186C8B15C0A1/
ls -la .Trash*
```

---

### Post by satimis on 2022-04-20
> **1fallen said:**
> Is this really an ISO drive??? IE:"cd /media/satimis/E0C8B186C8B15C0A1/PC1A_Data_20181231_20220430/1_PC1A_Data_Technical_20211231_20220430/Software_20211231_20220430**_/ISO/"_**
No this is NOT an ISO drive
This is the folder, named ISO for containing these 3 ISOs.  I haven't installed them.

This is an external HDD shared amongst other PCs.  The strange thing happened here is in this ISO folder there are other ISOs.  According to my recollection I can delete them on this ISO folders as well as on Trash.  Leaving behind are those 3 ISOs mentioned here.  Instead of "deleted" they are triplicated.

---

### Post by satimis on 2022-04-20
> **halogen2 said:**
> ....
Please do
```
cd /media/satimis/E0C8B186C8B15C0A1/
ls -la .Trash*
```
$ cd /media/satimis/E0C8B186C8B15C0A1/

satimis@PCIeSSD1T:/media/satimis/E0C8B186C8B15C0A1$ ls -la .Trash*```

total 4176
drwxrwxrwx 1 satimis satimis       0 Nov 20 13:23 .
drwxrwxrwx 1 satimis satimis   20480 Apr 20 13:21 ..
drwxrwxrwx 1 satimis satimis 4247552 Apr 20 23:08 expunged
drwxrwxrwx 1 satimis satimis    4096 Apr 20 20:24 files
drwxrwxrwx 1 satimis satimis    4096 Apr 20 23:20 info

```

---

### Post by #&amp;thj^% on 2022-04-20
we have too many repliers (confusion), I'm going to watch on the sideline for a bit.
but if it were me i would not delete from the location your suggesting.

---

### Post by &amp;KyT$0P# on 2022-04-20
I take it this is a NTFS formatted drive with only one [FONT=Courier New].Trash*[/FONT] folder?  Not seeing any permission based issue why you wouldn't be able to delete files from there.

What is the [FONT=Courier New].Trash*[/FONT] folder *actually* named?
```
echo .Trash*
```
It should have a number after it that matches the number after [FONT=Courier New]uid=[/FONT] in output of
```
id
```
Did you do the deletion on a different computer where your uid is not the same as your uid on your current computer?

In any case, in your place I would be tempted to try
```
rm -vR /media/satimis/E0C8B186C8B15C0A1/.Trash*
```

---

### Post by satimis on 2022-04-20
> **halogen2 said:**
> I take it this is a NTFS formatted drive with only one [FONT=Courier New].Trash*[/FONT] folder?  Not seeing any permission based issue why you wouldn't be able to delete files from there.

What is the [FONT=Courier New].Trash*[/FONT] folder *actually* named?
```
echo .Trash*
```
It should have a number after it that matches the number after [FONT=Courier New]uid=[/FONT] in output of
```
id
```
Did you do the deletion on a different computer where your uid is not the same as your uid on your current computer?

In any case, in your place I would be tempted to try
```
rm -vR /media/satimis/E0C8B186C8B15C0A1/.Trash*
```
$ echo .Trash*```

.Trash*

```

$ id```

uid=1000(satimis) gid=1000(satimis) groups=1000(satimis),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare),127(vboxusers)

```

$ rm -vR /media/satimis/E0C8B186C8B15C0A1/.Trash*
```

....
....
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/978644169': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/4023453966': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/4023454058': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/4023454297': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/4023454357': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/4023454520': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/3581407642': Input/output error
....
....

```

> 
Did you do the deletion on a different computer where your uid is not the same as your uid on your current computer?
Sorry I couldn't recall.  This external HDD is mounted on a docking and shared to be used on 3 PCs, all running Ubuntu 20.04

Regards

---

### Post by satimis on 2022-04-20
> **1fallen said:**
> we have too many repliers (confusion), I'm going to watch on the sideline for a bit.
but if it were me i would not delete from the location your suggesting.
What amazes me is;
If I don't connect the external HDD, Trash is empty.

At the beginning I used a long SATA cable and a long power cable extending to the outside the computer case to connect the external HDD.
(Remark: not for this HDD)

It worked and the transfer time was much faster.  But it is not a good solution for house-keeping, the external HDD was placed on the desk.  Then I purchased the Docking to mount the external HDD.

Regards

---

### Post by #&amp;thj^% on 2022-04-20
> **satimis said:**
> $ echo .Trash*```

.Trash*

```

$ id```

uid=1000(satimis) gid=1000(satimis) groups=1000(satimis),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare),127(vboxusers)

```

$ rm -vR /media/satimis/E0C8B186C8B15C0A1/.Trash*
```

....
....
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/978644169': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/4023453966': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/4023454058': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/4023454297': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/4023454357': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/4023454520': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/3581407642': Input/output error
....
....

```


Sorry I couldn't recall.  This external HDD is mounted on a docking and shared to be used on 3 PCs, all running Ubuntu 20.04

Regards

satimis I really hate what I'm about to suggest now but i have had to do this in ubuntu a time or two:
```
apt policy nautilus-admin
```
if nothing shows installed, yep install it:
```
sudo apt install nautilus-admin
``` 
then run after install:
```
nautilus -q
```
You "should now have admins rights in nautilus"
right click on that drive And select the option “Edit as Administrator”.
try to delete the trash from there.

---

### Post by satimis on 2022-04-20
> **1fallen said:**
> satimis I really hate what I'm about to suggest now but i have had to do this in ubuntu a time or two:
```
apt policy nautilus-admin
```
if nothing shows installed, yep install it:
```
sudo apt install nautilus-admin
``` 
then run after install:
```
nautilus -q
```
You "should now have admins rights in nautilus"
right click on that drive And select the option &#8220;Edit as Administrator&#8221;.
try to delete the trash from there.
$ apt policy nautilus-admin```

nautilus-admin:
  Installed: (none)
  Candidate: 1.1.9-3
  Version table:
     1.1.9-3 500
        500 [http://hk.archive.ubuntu.com/ubuntu](http://hk.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
        500 [http://hk.archive.ubuntu.com/ubuntu](http://hk.archive.ubuntu.com/ubuntu) focal/universe i386 Packages

```

$ sudo apt install nautilus-admin```

....
Unpacking gir1.2-nautilus-3.0:amd64 (1:3.36.3-0ubuntu1.20.04.1) ...
Selecting previously unselected package python3-nautilus.
Preparing to unpack .../python3-nautilus_1.2.3-1ubuntu1_amd64.deb ...
Unpacking python3-nautilus (1.2.3-1ubuntu1) ...
Selecting previously unselected package nautilus-admin.
Preparing to unpack .../nautilus-admin_1.1.9-3_all.deb ...
Unpacking nautilus-admin (1.1.9-3) ...
Setting up gir1.2-nautilus-3.0:amd64 (1:3.36.3-0ubuntu1.20.04.1) ...
Setting up python3-nautilus (1.2.3-1ubuntu1) ...
Setting up nautilus-admin (1.1.9-3) ...

```

$ nautilus -q

> right click on that drive And select the option &#8220;Edit as Administrator&#8221;.
no &#8220;Edit as Administrator&#8221; such an option
(pls see screenshot attached)

Regards

---

### Post by #&amp;thj^% on 2022-04-20
> **satimis said:**
> $ apt policy nautilus-admin```

nautilus-admin:
  Installed: (none)
  Candidate: 1.1.9-3
  Version table:
     1.1.9-3 500
        500 [http://hk.archive.ubuntu.com/ubuntu](http://hk.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
        500 [http://hk.archive.ubuntu.com/ubuntu](http://hk.archive.ubuntu.com/ubuntu) focal/universe i386 Packages

```

$ sudo apt install nautilus-admin```

....
Unpacking gir1.2-nautilus-3.0:amd64 (1:3.36.3-0ubuntu1.20.04.1) ...
Selecting previously unselected package python3-nautilus.
Preparing to unpack .../python3-nautilus_1.2.3-1ubuntu1_amd64.deb ...
Unpacking python3-nautilus (1.2.3-1ubuntu1) ...
Selecting previously unselected package nautilus-admin.
Preparing to unpack .../nautilus-admin_1.1.9-3_all.deb ...
Unpacking nautilus-admin (1.1.9-3) ...
Setting up gir1.2-nautilus-3.0:amd64 (1:3.36.3-0ubuntu1.20.04.1) ...
Setting up python3-nautilus (1.2.3-1ubuntu1) ...
Setting up nautilus-admin (1.1.9-3) ...

```

$ nautilus -q
no &#8220;Edit as Administrator&#8221; such an option
(pls see screenshot attached)

Regards
Are you currently the only one mounted to this drive?
try:
```
sudo nautiluls -q
```
to close that terminal you may need to use:
```
exit
```

---

### Post by &amp;KyT$0P# on 2022-04-20
> **satimis said:**
> ```

....
....
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/978644169': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/4023453966': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/4023454058': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/4023454297': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/4023454357': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/4023454520': Input/output error
rm: cannot remove '/media/satimis/E0C8B186C8B15C0A1/.Trash-1000/expunged/3581407642': Input/output error
....
....

```

That could be very bad.  Still assuming the filesystem is NTFS, what version of Windows do you sometimes use this drive with?  Try to check and repair the drive's filesystem using that same version of Windows.

If Windows has trouble with the filesystem or trouble repairing it, I would suggest investigating the drive's health using smartctl, starting with
```
sudo smartctl -a /dev/sdd
```
(Double check that the drive is indeed still sdd before running this.)

If you don't have smartctl, you can install it with
```
sudo apt-get install smartmontools
```

Do you have backups of all the important data currently on that drive?

---

### Post by satimis on 2022-04-20
> **1fallen said:**
> Are you currently the only one mounted to this drive?
Sorry, I don't catch.  I'm the only person using this computer

To read the internal HDD, I must start "File Manager"
-> Other Locations -> select 4.0 TB Volume

> 
try:
```
sudo nautiluls -q
```
to close that terminal you may need to use:
```
exit
```
Still the same, no “Edit as Administrator” such an option

---

### Post by #&amp;thj^% on 2022-04-20
> **satimis said:**
> Sorry, I don't catch.  I'm the only person using this computer


You had mentioned 3 others to share the drive?
if one or more of them are mounted that would stop the empty as well.
See halogen2 last reply, and give that a go, if you have a bootable windows install try to delete from there.

---

### Post by satimis on 2022-04-20
> **halogen2 said:**
> That could be very bad.  Still assuming the filesystem is NTFS, what version of Windows do you sometimes use this drive with?  Try to check and repair the drive's filesystem using that same version of Windows.

If Windows has trouble with the filesystem or trouble repairing it, I would suggest investigating the drive's health using smartctl, starting with
```
sudo smartctl -a /dev/sdd
```
(Double check that the drive is indeed still sdd before running this.)

If you don't have smartctl, you can install it with
```
sudo apt-get install smartmontools
```

Do you have backups of all the important data currently on that drive?
This is a dual-boot PC, Ubuntu 20.04 and Win10.  I never connected Win10 to external HDD before.

Win10 can't connect the internal HDD directly and must go through "ext2 volume manager" (if I remember correctly).  Even connected Win10 is only allowed to copy files from the internal HDD.  Win10 can't save files on the internet HDD of this Pc.

Sorry I don't have backup copy of the external HDD.  Most data on the external HDD are copy of the internal HDD.  The rests are data from another 2 PCs, say PC-2 and PC-3

---

### Post by #&amp;thj^% on 2022-04-20
> **satimis said:**
> This is a dual-boot PC, Ubuntu 20.04 and Win10.  I never connected Win10 to external HDD before.

Win10 can't connect the internal HDD directly and must go through "virt2 volume manager" (if I remember correctly).  Even connected Win10 is only allowed to copy files from the internal HDD.  Win10 can't save files on the internet HDD of this Pc.

Sorry I don't have backup copy of the external HDD.  Most data on the external HDD are copy of the internal HDD.  The rests are data from another 2 PCs, say PC-2 and PC-3
Bingo, I now feel better suggesting this:
```
sudo -H nautilus
```
your now root make good and sure you only remove what was needed "Trash"

---

### Post by satimis on 2022-04-20
> **1fallen said:**
> You had mentioned 3 others to share the drive?
if one or more of them are mounted that would stop the empty as well.
See halogen2 last reply, and give that a go, if you have a bootable windows install try to delete from there.
Whether you referred to other drives?

on  the right column:
Computer (main drive running Ubuntu 20.04)
4.0 TB Volume (internal HDD for data storage)
999 GB Volume (SSD running Windows10)
500 GB Volume (SSD also running Ubuntu 20.04)

They are not connected unless
-> Other Locations -> select any of them

Windows 10 can't connect internal HDD directly and must via "ext2 volume manager.  Even connected Windows 10 can only copy files from the internal HDD and can't save files on it.

---

### Post by satimis on 2022-04-20
> **1fallen said:**
> Bingo, I now feel better suggesting this:
```
sudo -H nautilus
```
your now root make good and sure you only remove what was needed "Trash"
$ sudo -H nautilus```

** (org.gnome.Nautilus:13388): WARNING **: 10:26:47.277: Unable to get contents of the bookmarks file: Error opening file /root/.gtk-bookmarks: No such file or directory

** (org.gnome.Nautilus:13388): WARNING **: 10:26:47.277: Unable to get contents of the bookmarks file: Error opening file /root/.gtk-bookmarks: No such file or directory
Nautilus-Share-Message: 10:26:47.340: Called "net usershare info" but it failed: Failed to execute child process “net” (No such file or directory)

```

-> Trash
Warning
(pls see screenshot)

---

### Post by #&amp;thj^% on 2022-04-20
you need to follow post # 28 smartctl
something is not looking so favorable ATM

---

### Post by satimis on 2022-04-20
> **1fallen said:**
> you need to follow post # 28 smartctl
something is not looking so favorable ATM
I can't resolve why there is connection with Windows.  Windows can't connect the external drive on ext4 format directly.  It must go through a software "ext2 volume manager".  Besides, even connected, Windows can only copy files from the external drive but can't save files on it.

Just started Windows10 on this PC to confirm above.

This is a brand-new 4TB WD magnetic HDD, purchased about 2~3 months ago solely for data storage.  All operation systems, either Linux or Windows are installed and running on SATA SSD and NVMe PCIe SSD of all my PCs.  I'm sure that I formatted this external HDD on ext4 system only.

---

### Post by satimis on 2022-04-20
Hi all,

I'll be pending the problem on this posting a while, if without a solution.

I'm prepared to build a new AMD Ryzen 9 12-core PC. Then I'll add this external HDD to the new PC as internal drive to check what will happen. I still have old 2TB WD SATA HDD and old 1TB SATA SSD.  I can use them as external HDD

New PC - please see my posting;
Components for a Dual-boot Desktop PC
[https://ubuntuforums.org/showthread.php?t=2473386](https://ubuntuforums.org/showthread.php?t=2473386)

I'll start shopping components after the release of Ubuntu 22.04 and becoming stable.  First I'll test Ubuntu 22.04 on a VM of Oracle VirtualBox

The new PC shall be used as follows;
1)
To build a Linux system - LFS
About building your own Linux system - LFS 
[https://ubuntuforums.org/showthread.php?t=2473761&highlight=satimis](https://ubuntuforums.org/showthread.php?t=2473761&highlight=satimis)

2) To install cPanel
Can cPanel be installed on Ubuntu 20.04 ?
[https://ubuntuforums.org/showthread.php?t=2473652&highlight=satimis](https://ubuntuforums.org/showthread.php?t=2473652&highlight=satimis)

Anyway, lot of thanks for your advice

Regards

---

### Post by #&amp;thj^% on 2022-04-21
satimis the reference to smartctl has nothing to do Windows, we just can't figure out why the trash is so locked-up, we've even gone somewhat astray with sudo here.
We just don't want you loose the data you now have on that storage drive.
Demo on smartctl:
```
sudo smartctl -a /dev/sdb

smartctl 7.3 2022-02-28 r5338 [x86_64-linux-5.17.4-AMD] (local build)
Copyright (C) 2002-22, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Number:                       WDC PC SN730 SDBQNTY-256G-1001
Serial Number:                      201429806191
Firmware Version:                   11170101
PCI Vendor/Subsystem ID:            0x15b7
IEEE OUI Identifier:                0x001b44
Total NVM Capacity:                 256,060,514,304 [256 GB]
Unallocated NVM Capacity:           0
Controller ID:                      8215
NVMe Version:                       1.3
Number of Namespaces:               1
Namespace 1 Size/Capacity:          256,060,514,304 [256 GB]
Namespace 1 Formatted LBA Size:     512
Namespace 1 IEEE EUI-64:            001b44 8b46045ddb
Local Time is:                      Thu Apr 21 09:12:33 2022 MDT
Firmware Updates (0x14):            2 Slots, no Reset required
Optional Admin Commands (0x0017):   Security Format Frmw_DL Self_Test
Optional NVM Commands (0x005f):     Comp Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat Timestmp
Log Page Attributes (0x1e):         Cmd_Eff_Lg Ext_Get_Lg Telmtry_Lg Pers_Ev_Lg
Maximum Data Transfer Size:         128 Pages
Warning  Comp. Temp. Threshold:     84 Celsius
Critical Comp. Temp. Threshold:     88 Celsius
Namespace 1 Features (0x02):        NA_Fields

Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     5.00W       -        -    0  0  0  0        0       0
 1 +     3.50W       -        -    1  1  1  1        0       0
 2 +     3.00W       -        -    2  2  2  2        0       0
 3 -   0.0700W       -        -    3  3  3  3     4000   10000
 4 -   0.0035W       -        -    4  4  4  4     4000   40000

Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         2
 1 -    4096       0         1

=== START OF SMART DATA SECTION ===
**[COLOR="#FF0000"]SMART overall-health self-assessment test result: PASSED[/COLOR]**

SMART/Health Information (NVMe Log 0x02)
Critical Warning:                   0x00
Temperature:                        47 Celsius
Available Spare:                    100%
Available Spare Threshold:          10%
Percentage Used:                    7%
Data Units Read:                    19,231,507 [9.84 TB]
Data Units Written:                 17,551,299 [8.98 TB]
Host Read Commands:                 440,775,960
Host Write Commands:                384,419,435
Controller Busy Time:               706
Power Cycles:                       1,256
Power On Hours:                     2,115
Unsafe Shutdowns:                   171
Media and Data Integrity Errors:    0
Error Information Log Entries:      1
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0
Thermal Temp. 1 Transition Count:   3
Thermal Temp. 2 Transition Count:   1
Thermal Temp. 1 Total Time:         584
Thermal Temp. 2 Total Time:         180

Warning: NVMe Get Log truncated to 0x200 bytes, 0x200 bytes zero filled
Error Information (NVMe Log 0x01, 16 of 256 entries)
No Errors Logged

```
important info is: "SMART overall-health self-assessment test result: PASSED" along with:
```
Available Spare:                    100%
Available Spare Threshold:          10%
Percentage Used:                    7%
Data Units Read:                    19,231,507 [9.84 TB]
Data Units Written:                 17,551,299 [8.98 TB]
Unsafe Shutdowns:                   171
Media and Data Integrity Errors:    0
Error Information Log Entries:      1 
```

Now my 2 cents worth for your new build with cpanel: [https://www.how2shout.com/linux/how-to-install-whm-cpanel-on-ubuntu-20-04-lts-linux/](https://www.how2shout.com/linux/how-to-install-whm-cpanel-on-ubuntu-20-04-lts-linux/)
I'm in the dark when it comes to cpanel, I've not had a reason to use it due to it's OS reliant for CentOS. *(at the time I first looked at it)*

---

### Post by satimis on 2022-04-22
Hi 1fallen

Thanks for your detail reply.

It is the same when I plugined this external HDD mounted on locking to another PC.  The Trash was partially locked.  Other deleted data can be emptied on the Trash, except these 3 ISOs.  They seems permanently locked.

I'll try connecting it as internal HDD to my new PC as mentioned Post #37.  If it is still the same I'll copy all its data to the HDD of the new PC, except these 3 ISOs.  Afterwards I'll run "fdisk" to format the whole HDD

Regards

---

