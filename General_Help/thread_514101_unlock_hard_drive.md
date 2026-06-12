---
title: "unlock hard drive"
date: 2007-07-31
forum: General Help
---

### Post by ali780 on 2007-07-31
Hi
# partition on my hard drive is locked and I can not write or delete on it. How can I unlock these partitions?
Thanks

---

### Post by ali780 on 2007-07-31
3 partition

---

### Post by Fallen_62 on 2007-07-31
What file system is it using...?

---

### Post by ali780 on 2007-07-31
I don't understand what do you say. When I want copy something on this partition I received an error, that say I am not allowed to write on this partition because this partition is write protect.

---

### Post by nitro_n2o on 2007-07-31
This normally happens if you have an NTFS partition (the one for windows) go to System->Administration->Synaptic then search for NTFS and choose the NTFS configuration tool for download. When done, go to Applicatoins->System tools -> NTFS configuration tool enter your root password and then tick the first two options

---

### Post by ali780 on 2007-07-31
Thanks
But this partition is not a NTFS partion it is FAT32

---

### Post by nitro_n2o on 2007-07-31
maybe it is a permisson problem then.. 
try writing to the file using sudo if that is the case  you need to change the permissions on the drive

---

### Post by ali780 on 2007-07-31
how can I change the permission? I think this is a permission problem.

---

### Post by nitro_n2o on 2007-07-31
or maybe it's not mounted :) 
check out this 
[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)
if you haven't set a mount point for the partition during installation

---

### Post by nitro_n2o on 2007-07-31
> **ali780 said:**
> how can I change the permission? I think this is a permission problem.

sudo chown <username> /dev/<partition> [this will change to ownership 
sudo chmod +w /dev/<partions> [will make it writable]

---

### Post by ali780 on 2007-07-31
No it is mounted. I think it is a permission problem. Could you say me how can I change the permission?

---

### Post by nitro_n2o on 2007-07-31
> **ali780 said:**
> No it is mounted. I think it is a permission problem. Could you say me how can I change the permission?

```
sudo chmod +w /dev/sda3 
```

replace /dev/sda3 with your paritition 
to know where is you partition do ```
sudo fdisk -l
```
hope that helps

---

### Post by ali780 on 2007-07-31
when I try to copy this is the error
cannot create regular file `/media/sda5/Temp/devcpp-4.9.9.2_setup.exe': Read-only file system

---

### Post by ali780 on 2007-07-31
when I used sudo chmod +w .....
This error appeared
changing permissions of `/media/sda5/': Read-only file system

---

### Post by nitro_n2o on 2007-07-31
what is the output of ```
ls -all /media/sda5
```

---

### Post by nitro_n2o on 2007-07-31
and try this 
```
sudo chown -R <ur_user_name> /media/sda5
```

---

### Post by ali780 on 2007-07-31
The output is
total 32
dr-xr-x---  1 root plugdev 4096 2007-07-25 20:58 .
drwxr-xr-x 10 root root    4096 2007-07-31 08:46 ..
-r-xr-x---  1 root plugdev   14 2007-03-29 22:50 Narcis53.dat
-r-xr-x---  1 root plugdev 9216 2007-06-07 21:36 NARCIS53.RPT
-r-xr-x---  1 root plugdev 1024 2007-03-29 22:50 NARCIS53.SYS
dr-xr-x---  1 root plugdev    0 2007-04-14 06:52 $RECYCLE.BIN
dr-xr-x---  1 root plugdev    0 2007-04-15 09:01 RECYCLER
dr-xr-x---  1 root plugdev 4096 2007-02-11 10:54 System Volume Information
dr-xr-x---  1 root plugdev 4096 2007-06-09 10:02 Temp

---

### Post by nitro_n2o on 2007-07-31
you can't change the permission without sudo. Actually you need to do this: 

activate your root account 
```
sudo passwd su
<enter a new passwd>
<repeat passwd> 
su
chown -R <ur_user_name> /media/sda5/
chmod +w /media/sda5/
```
check your new permission 
```
ls -all /media/sda5
```
you should see something like this 
drwxrwx--w 1 your_usr_name plugdev 4096 2007-07-25 20:58 .

---

### Post by ali780 on 2007-07-31
> sudo passwd su
<enter a new passwd>
<repeat passwd> 
I don't understand this part. what is passwd?

---

### Post by strabes on 2007-07-31
> sudo passwd su
<enter a new passwd>
<repeat passwd>
I don't understand this part. what is passwd?

It will prompt you for your password. Just type in your user password that you use to log in. For more information see [this page](http://www.psychocats.net/ubuntu/passwordinterminal) and [this page](http://www.psychocats.net/ubuntu/terminal).


Paste the output of the following command please. It will help us help you and will most likely let us tell you the exact commands to run.```
sudo fdisk -l
```

---

### Post by ali780 on 2007-07-31
This is the out put of sudo fdisk -l
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         637     5116671    7  HPFS/NTFS
/dev/sda2             638        9964    74919127+   f  W95 Ext'd (LBA)
/dev/sda5             638        9964    74919096    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       26526   213062062+   f  W95 Ext'd (LBA)
/dev/sdb2   *       26527       30401    31125937+   7  HPFS/NTFS
/dev/sdb5               2       12240    98309736    b  W95 FAT32
/dev/sdb6           12241       22348    81192478+   b  W95 FAT32
/dev/sdb7           22349       26395    32507496   83  Linux
/dev/sdb8           26396       26526     1052226   82  Linux swap / Solaris

---

### Post by strabes on 2007-07-31
Which partition are you trying to copy files to? Please use its /dev location from ```
sudo fdisk -l
```.

---

### Post by ali780 on 2007-07-31
sda5

---

### Post by ali780 on 2007-07-31
Thank you everybody.
 I fixed my problem.

---

