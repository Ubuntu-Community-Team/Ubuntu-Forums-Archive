---
title: "btrfs write permission to external ext4 hard drive"
date: 2023-01-27
forum: General Help
---

### Post by monkeybrain20122 on 2023-01-27
Hi, 

In one of my laptop I have Ubuntu 22.04 installed in the btrfs file system. I have an external hard disk formatted to ext4, but I cannot set up write permission to the disk. It mounts when plugged in, I can copy files from there to my laptop but cannot write to it, delete or create file in it. I cannot change the permission with sudo chown or sudo chmod  (write only file system)


 I can access and change permission of the hard drive from another computer where Ubuntu is also installed (ext4). I changed a folder's permission to 777 (sudo chmod -R 777 /path/to/folder) but I still can't write to it from the first laptop.

the permission looks , with ls -l from the first laptop (formatted to btrfs), the owner has the same name in both computer

```
drwxrwxrwx  3 mb mb       4096 Sep 15  2021 'personal'

```

I think this is due to the btrfs file system in the laptop and some extra care is needed (like doing something with fstab?)

Help is appreciated. Thanks.

---

### Post by #&amp;thj^% on 2023-01-27
This has to be a Ubuntu Gnome thing then, I have no issues with any of that.
```
inxi -p | grep btrfs
  ID-1: / size: 237.02 GiB used: 25.64 GiB (10.8%) fs: btrfs dev: /dev/dm-2
  ID-2: /boot size: 977 MiB used: 225.7 MiB (23.1%) fs: btrfs dev: /dev/sdb2

```
I'm not sure I would mess with fstab just yet
I can write to delete, change what I want to here:
```
df -hT
Filesystem                       Type      Size  Used Avail Use% Mounted on
udev                             devtmpfs  3.8G     0  3.8G   0% /dev
tmpfs                            tmpfs     782M  2.3M  779M   1% /run
/dev/mapper/kaisenlinux--vg-root btrfs     238G   26G  208G  12% /
tmpfs                            tmpfs     3.9G     0  3.9G   0% /dev/shm
tmpfs                            tmpfs     5.0M   20K  5.0M   1% /run/lock
/dev/sdb2                        btrfs     977M  226M  642M  27% /boot
/dev/nvme0n1p1                   vfat     1022M  272M  751M  27% /boot/efi
mypool                           zfs       450G  9.8G  440G   3% /mypool
tmpfs                            tmpfs     782M  196K  781M   1% /run/user/1000
/dev/sde1                        fuseblk   3.7T  2.4T  1.4T  64% /media/me/My Passport
/dev/sdi1                        ntfs3     4.6T  4.4T  176G  97% /media/me/My Passport1

```
EDIT: guessing here because I'm not Gnome/Snap user but, try to set yourself as the owner by doing this:

```
sudo chown username:username /media/mountpoint
```

---

### Post by monkeybrain20122 on 2023-01-27
Hi, I have deleted all snap and I am using unity instead of gnome 


```
inxi -p | grep btrfs
  ID-1: / size: 237.97 GiB used: 84.06 GiB (35.3%) fs: btrfs
  ID-3: /home size: 237.97 GiB used: 84.06 GiB (35.3%) fs: btrfs

```

```

df -hT
Filesystem     Type   Size  Used Avail Use% Mounted on
tmpfs          tmpfs  1.6G  2.1M  1.6G   1% /run
/dev/nvme0n1p2 btrfs  238G   85G  153G  36% /
tmpfs          tmpfs  7.8G  208K  7.8G   1% /dev/shm
tmpfs          tmpfs  5.0M  4.0K  5.0M   1% /run/lock
/dev/nvme0n1p2 btrfs  238G   85G  153G  36% /home
/dev/nvme0n1p1 vfat   511M   15M  497M   3% /boot/efi
tmpfs          tmpfs  1.6G  316K  1.6G   1% /run/user/1000
/dev/sda1      ext4   917G  459G  412G  53% /media/mb/bkup
```






It doesn't work
```
$sudo chown mb:mb "/media/mb/bkup/toshiba/personal"
chown: changing ownership of '/media/mb/bkup/toshiba/personal': Read-only file system


$ chmod -R 777 "/media/mb/bkup/toshiba/personal"
chmod: changing permissions of '/media/mb/bkup/toshiba/personal ': Read-only file system
chmod: changing permissions of '/media/mb/bkup/toshiba/personal /pascal.doc': Read-only file system
chmod: changing permissions of '/media/mb/bkup/toshiba/personal /pptc054.pdf': Read-only file system
chmod: changing permissions of '/media/mb/bkup/toshiba/personal /intel-cred': Read-only file system
chmod: changing permissions of '/media/mb/bkup/toshiba/personal /Camping checklist.docx': Read-only file system
```


Still can't write to it.

---

### Post by #&amp;thj^% on 2023-01-27
Crap I hate seeing this " **Read-only file system**" hows your disk health?
Something in the current system is throwing it into protection mode.

---

### Post by monkeybrain20122 on 2023-01-27
> **1fallen said:**
> Crap I hate seeing this " **Read-only file system**" hows your disk health?
Something in the current system is throwing it into protection mode.

The disk is fine, I can read and write to it from another laptop also with Ubuntu but formatted to ext4

**Edited:** there is another external disk formatted to ntfs, I can write and read with no issue from this laptop.

---

### Post by #&amp;thj^% on 2023-01-27
OK then you'll have to look at "Something in the current system is throwing it into protection mode."
FTR I did notice you was able to read and write from another system hence the above.

---

### Post by monkeybrain20122 on 2023-01-27
Hi,

I just plugged it in and removed it. I got this
```
sudo dmesg | tail
[sudo] password for mb: 
[21997.731027] EXT4-fs error (device sda1): ext4_mb_generate_buddy:1145: group 764, block bitmap and bg descriptor inconsistent: 0 vs 32768 free clusters
[21997.742151] EXT4-fs error (device sda1): ext4_mb_generate_buddy:1145: group 763, block bitmap and bg descriptor inconsistent: 0 vs 32768 free clusters
[21997.753262] EXT4-fs error (device sda1): ext4_mb_generate_buddy:1145: group 762, block bitmap and bg descriptor inconsistent: 0 vs 32768 free clusters
[21997.764351] EXT4-fs error (device sda1): ext4_mb_generate_buddy:1145: group 761, block bitmap and bg descriptor inconsistent: 0 vs 32768 free clusters
[21997.775454] EXT4-fs error (device sda1): ext4_mb_generate_buddy:1145: group 760, block bitmap and bg descriptor inconsistent: 0 vs 32768 free clusters
[21997.786732] EXT4-fs error (device sda1): ext4_mb_generate_buddy:1145: group 759, block bitmap and bg descriptor inconsistent: 0 vs 32768 free clusters
[21997.797811] EXT4-fs error (device sda1): ext4_mb_generate_buddy:1145: group 758, block bitmap and bg descriptor inconsistent: 0 vs 32768 free clusters
[22014.293470] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[22014.541331] sd 2:0:0:0: [sda] Synchronize Cache(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[22014.589324] usb 2-1: USB disconnect, device number 7
```

---

### Post by #&amp;thj^% on 2023-01-28
This is the second heads up Ive noticed from your current OS:
```
[22014.541331] sd 2:0:0:0: [sda] Synchronize Cache(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
```
In my many years, this has always had a bad ending. (Not what you want to hear but it keeps on begging your attention)
Feel free to add a bug-report
monkeybrain20122 I'm just lost to provide with any more suggestions here.

---

### Post by monkeybrain20122 on 2023-01-28
Is it a problem with the os or the external disk?

---

### Post by #&amp;thj^% on 2023-01-28
I'm on the fence right now, you can access it and read write from another Ubuntu OS.
I see how the BTRFS would pop in first as suspect, but it's not to blame here.
I just caught wind that you may be using Nemo FM on Unity right?

---

### Post by monkeybrain20122 on 2023-01-28
Yes I am using nemo on Unity. But it is the same in the other laptop as well. The only difference is the other laptop has Ubuntu 20.04 and this one 22.04.

---

### Post by monkeybrain20122 on 2023-01-28
This laptop has no problem writing to another external disk formatted in ntfs. If It is the external drive's problem I won't be too worried. I have multiple backup so I can always transfer the stuffs elsewhere.

---

### Post by #&amp;thj^% on 2023-01-28
> **monkeybrain20122 said:**
>  If It is the external drive's problem I won't be too worried. I have multiple backup so I can always transfer the stuffs elsewhere.

Good enough for me. ;) And just for safety sake I would back it up soon, or while the getting is good.

---

### Post by monkeybrain20122 on 2023-01-28
Hi, 1fallen

I popped the hard drive in the other laptop (where write works) and do a dmesg and I got the same errors ! So somehow the other system doesn't turn it into read only

 ```
sudo dmesg | tail
[sudo] password for mb: 
[1408058.551951] EXT4-fs error (device sda1): ext4_mb_generate_buddy:1141: group 764, block bitmap and bg descriptor inconsistent: 0 vs 32768 free clusters
[1408058.551960] EXT4-fs error (device sda1): ext4_mb_generate_buddy:1141: group 763, block bitmap and bg descriptor inconsistent: 0 vs 32768 free clusters
[1408058.551964] EXT4-fs error (device sda1): ext4_mb_generate_buddy:1141: group 762, block bitmap and bg descriptor inconsistent: 0 vs 32768 free clusters
[1408058.551981] EXT4-fs error (device sda1): ext4_mb_generate_buddy:1141: group 761, block bitmap and bg descriptor inconsistent: 0 vs 32768 free clusters
[1408058.551985] EXT4-fs error (device sda1): ext4_mb_generate_buddy:1141: group 760, block bitmap and bg descriptor inconsistent: 0 vs 32768 free clusters
[1408058.551989] EXT4-fs error (device sda1): ext4_mb_generate_buddy:1141: group 759, block bitmap and bg descriptor inconsistent: 0 vs 32768 free clusters
[1408058.552012] EXT4-fs error (device sda1): ext4_mb_generate_buddy:1141: group 758, block bitmap and bg descriptor inconsistent: 0 vs 32768 free clusters
[1408077.901227] sd 4:0:0:0: [sda] Synchronizing SCSI cache
[1408077.901408] sd 4:0:0:0: [sda] Synchronize Cache(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[1408077.937420] usb 2-5: USB disconnect, device number 14
```

---

### Post by #&amp;thj^% on 2023-01-28
> **monkeybrain20122 said:**
> So somehow the other system doesn't turn it into read only

 

Understood, I stand by my back-up now though. It just makes good sense to move it out of the way now. and regret free. :)

---

### Post by monkeybrain20122 on 2023-01-28
> **1fallen said:**
> Understood, I stand by my back-up now though. It just makes good sense to move it out of the way now. and regret free. :)

Yeah I will do that. I am just wondering why the two Ubuntu's don't behave the same.

Thanks for all the help!

---

### Post by #&amp;thj^% on 2023-01-28
Happy to help, Code gets improved, also brings in minor bugs drivers are added and feature are added as new....who knows.
```
stat /mypool Documents Pictures /home
  File: /mypool
  Size: 6         	Blocks: 21         IO Block: 16384  directory
Device: 0,44	Inode: 34          Links: 6
Access: (0755/drwxr-xr-x)  Uid: ( 1000/      me)   Gid: ( 1000/      me)
Access: 2023-01-28 12:35:59.131560596 -0700
Modify: 2023-01-28 12:36:18.039535085 -0700
Change: 2023-01-28 12:36:18.039535085 -0700
 Birth: 2023-01-24 12:18:33.184667096 -0700
  File: Documents
  Size: 1728      	Blocks: 0          IO Block: 4096   directory
Device: 0,26	Inode: 575380      Links: 1
Access: (0755/drwxr-xr-x)  Uid: ( 1000/      me)   Gid: ( 1000/      me)
Access: 2023-01-28 12:17:47.325135733 -0700
Modify: 2023-01-28 12:13:58.405481278 -0700
Change: 2023-01-28 12:13:58.405481278 -0700
 Birth: 2022-12-27 14:22:21.985394436 -0700
  File: Pictures
  Size: 224       	Blocks: 0          IO Block: 4096   directory
Device: 0,26	Inode: 575382      Links: 1
Access: (0755/drwxr-xr-x)  Uid: ( 1000/      me)   Gid: ( 1000/      me)
Access: 2023-01-28 11:00:50.497064095 -0700
Modify: 2023-01-28 10:21:55.483546148 -0700
Change: 2023-01-28 10:21:55.483546148 -0700
 Birth: 2022-12-27 14:22:21.985394436 -0700
  File: /home
  Size: 4         	Blocks: 0          IO Block: 4096   directory
Device: 0,26	Inode: 3802        Links: 1
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2023-01-28 11:00:08.193118683 -0700
Modify: 2022-12-27 07:17:26.594922586 -0700
Change: 2022-12-27 07:17:26.594922586 -0700
 Birth: 2022-12-27 07:05:21.791379202 -0700


```
maybe for a compare, but I doubt it will change anything.

---

### Post by monkeybrain20122 on 2023-01-28
From the 22.04 laptop (cannot write)

```
stat / Documents Pictures /home
  File: /
  Size: 164           Blocks: 0          IO Block: 4096   directory
Device: 1ch/28d    Inode: 256         Links: 1
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2023-01-28 13:13:10.917483324 -0500
Modify: 2023-01-10 05:18:01.679257175 -0500
Change: 2023-01-10 05:18:01.679257175 -0500
 Birth: 2023-01-10 03:27:27.829761858 -0500
  File: Documents
  Size: 116           Blocks: 0          IO Block: 4096   directory
Device: 27h/39d    Inode: 357         Links: 1
Access: (0755/drwxr-xr-x)  Uid: ( 1000/ mb)   Gid: ( 1000/ mb)
Access: 2023-01-27 21:44:04.960115802 -0500
Modify: 2023-01-24 18:45:33.971107269 -0500
Change: 2023-01-24 18:45:33.971107269 -0500
 Birth: 2023-01-10 03:35:46.616520814 -0500
  File: Pictures
  Size: 0             Blocks: 0          IO Block: 4096   directory
Device: 27h/39d    Inode: 359         Links: 1
Access: (0755/drwxr-xr-x)  Uid: ( 1000/ mb)   Gid: ( 1000/ mb)
Access: 2023-01-28 15:21:20.622248921 -0500
Modify: 2023-01-28 15:23:40.281365498 -0500
Change: 2023-01-28 15:23:40.281365498 -0500
 Birth: 2023-01-10 03:35:46.616520814 -0500
  File: /home
  Size: 14            Blocks: 0          IO Block: 4096   directory
Device: 27h/39d    Inode: 256         Links: 1
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2023-01-28 12:51:12.365776220 -0500
Modify: 2023-01-10 03:31:17.691639287 -0500
Change: 2023-01-10 03:31:17.691639287 -0500
 Birth: 2023-01-10 03:27:27.853798523 -0500
```


on 20.04 laptop (write works)

```
 stat / Documents Pictures /home
  File: /
  Size: 4096          Blocks: 8          IO Block: 4096   directory
Device: 10302h/66306d    Inode: 2           Links: 20
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2023-01-28 12:44:25.189641081 -0500
Modify: 2022-10-09 21:24:44.881364090 -0400
Change: 2022-10-09 21:24:44.881364090 -0400
 Birth: -
  File: Documents
  Size: 4096          Blocks: 8          IO Block: 4096   directory
Device: 10302h/66306d    Inode: 20226104    Links: 17
Access: (0755/drwxr-xr-x)  Uid: ( 1000/ mb)   Gid: ( 1000/ mb)
Access: 2023-01-27 15:48:10.332466020 -0500
Modify: 2023-01-04 02:01:46.696584241 -0500
Change: 2023-01-04 02:01:46.696584241 -0500
 Birth: -
  File: Pictures
  Size: 4096          Blocks: 8          IO Block: 4096   directory
Device: 10302h/66306d    Inode: 19541046    Links: 9
Access: (0755/drwxr-xr-x)  Uid: ( 1000/ mb)   Gid: ( 1000/ mb)
Access: 2023-01-27 15:48:10.316466297 -0500
Modify: 2022-12-15 21:53:00.297808219 -0500
Change: 2022-12-15 21:53:00.297808219 -0500
 Birth: -
  File: /home
  Size: 4096          Blocks: 8          IO Block: 4096   directory
Device: 10302h/66306d    Inode: 19529729    Links: 3
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2023-01-19 08:52:57.501575821 -0500
Modify: 2021-05-20 03:06:21.000000000 -0400
Change: 2022-01-17 18:14:16.843373394 -0500
 Birth: -


```


Have to edit the post since I can't post from two computers simultaneously. :)

---

### Post by #&amp;thj^% on 2023-01-28
From the can't (btrfs)
```
 File: /
  Size: 164           Blocks: 0          IO Block: 4096   directory
Device: 1ch/28d    Inode: 256         Links: 1
```
Mine:
```
stat /
  File: /
  Size: 258       	Blocks: 0          IO Block: 4096   directory
Device: 0,26	Inode: 256         Links: 1
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2023-01-28 11:02:41.284920371 -0700
Modify: 2023-01-28 11:02:41.244920423 -0700
Change: 2023-01-28 11:02:41.244920423 -0700
 Birth: 2022-12-27 07:05:13.511338723 -0700

```
So that part looks good.

from the can (ext4)
```
File: /
  Size: 4096          Blocks: 8          IO Block: 4096   directory
Device: 10302h/66306d    Inode: 2           Links: 20
```
This must be a ext4 format, is that right?
sorry I tend to just go on and on, but nothing showing here is related to the orinigal topic.

---

### Post by monkeybrain20122 on 2023-01-28
> **1fallen said:**
> From the can't (btrfs)
```
 File: /
  Size: 164           Blocks: 0          IO Block: 4096   directory
Device: 1ch/28d    Inode: 256         Links: 1
```
Mine:
```
stat /
  File: /
  Size: 258           Blocks: 0          IO Block: 4096   directory
Device: 0,26    Inode: 256         Links: 1
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2023-01-28 11:02:41.284920371 -0700
Modify: 2023-01-28 11:02:41.244920423 -0700
Change: 2023-01-28 11:02:41.244920423 -0700
 Birth: 2022-12-27 07:05:13.511338723 -0700

```
So that part looks good.

from the can (ext4)
```
File: /
  Size: 4096          Blocks: 8          IO Block: 4096   directory
Device: 10302h/66306d    Inode: 2           Links: 20
```
This must be a ext4 format, is that right?
sorry I tend to just go on and on, but nothing showing here is related to the orinigal topic.

Yes, that's right.

I think the original issue is basically solved, I just need to grab a new hd?

No, I don't mind going off topic. I learned quite a lot in the past from that kind of tangents, sometimes they are more interesting than the original problem.

Thanks for the patience again.

---

