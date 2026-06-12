---
title: "Files - Other Locations - missing removable/hard drives"
date: 2021-05-12
forum: General Help
---

### Post by dwarthog on 2021-05-12
I just noticed that when I open Files then open "Other Locations", I no longer see my attached USB drives or my other hard files. 

This has to be a very recent change since I was able to see these drives two days ago. 

The drives are attached and do show up when I use the Disks utility program. 

Anyone know what's changed and what will allow me to see those disks again from the Files program?

Edit:

Fstab output

cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdj1 during installation
UUID=b8dcc06f-3bf8-4990-97cf-ce2e12a1704d /boot           ext4    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by TheFu on 2021-05-13
The fstab file doesn't have any clear references to other non-OS storage.

```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
will show the devices, file system types, and some other useful information.  Post using 'code tags' like I have above. Output from lsblk needs the columns to line up - that's what *code tags* does.  [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

BTW, you are using LVM for the OS. You might want to use it for external storage too. Lots of flexibility in doing that.

---

### Post by Dennis N on 2021-05-13
> I just noticed that when I open Files then open "Other Locations", I no longer see my attached USB drives or my other hard files.
It's not clear what you mean by "hard files".
"Other Locations" would not show external USB drives. They are displayed in the side pane of Files when they are detected.
"Other Locations" SHOULD show block devices with mountable file systems on internal drives - whether used for data or other operating systems.

---

### Post by dwarthog on 2021-05-13
> **TheFu said:**
> The fstab file doesn't have any clear references to other non-OS storage.

```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
will show the devices, file system types, and some other useful information.  Post using 'code tags' like I have above. Output from lsblk needs the columns to line up - that's what *code tags* does.  [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

BTW, you are using LVM for the OS. You might want to use it for external storage too. Lots of flexibility in doing that.


Here is the output from the command you provided. And thanks! 

```
NAME                      SIZE TYPE  FSTYPE      MOUNTPOINT
fd0                         4K disk              
sda                     279.5G disk              
&#9500;&#9472;sda1                    500M part  ext4        
&#9492;&#9472;sda2                    279G part  crypto_LUKS 
sdb                     931.5G disk              
&#9492;&#9472;sdb1                  931.5G part  ntfs        
sdh                     111.8G disk              
&#9492;&#9472;sdh1                  111.8G part  vfat        
sdi                     465.8G disk              
&#9492;&#9472;sdi1                  465.8G part  ntfs        
sdj                     465.8G disk              
&#9500;&#9472;sdj1                    731M part  ext4        /boot
&#9500;&#9472;sdj2                      1K part              
&#9492;&#9472;sdj5                    465G part  crypto_LUKS 
  &#9492;&#9472;sdj5_crypt            465G crypt LVM2_member 
    &#9500;&#9472;ubuntu--vg-root   464.1G lvm   ext4        /
    &#9492;&#9472;ubuntu--vg-swap_1   976M lvm   swap        [SWAP]
sdk                       1.8T disk              
&#9492;&#9472;sdk1                    1.8T part  crypto_LUKS 
sr0                      1024M rom               
sr1                      1024M rom               

```

I just realized the two USB storage devices I have attached isn't showing up as mounted either.

---

### Post by dwarthog on 2021-05-13
> **Dennis N said:**
> It's not clear what you mean by "hard files".
"Other Locations" would not show external USB drives. They are displayed in the side pane of Files when they are detected.
"Other Locations" SHOULD show block devices with mountable file systems on internal drives - whether used for data or other operating systems.

Sorry about my poor/inaccurate choice of words. Old words are hard to stop using at times. To really date myself, I still use CRT when describing a display and get some very strange looks... ;)

You are correct, the two USB storage devices should show on the side pane, and they are no longer there. 

The  block devices, other internal drives used for data storage,  are no longer showing up in the "Other Locations" as you also correctly state they should.

---

### Post by TheFu on 2021-05-13
From the lsblk output,which partitions do you expect to see?
The encrypted partitions need to be "opened" before any file system inside can be seen or accessed.

---

### Post by dwarthog on 2021-05-13
> **TheFu said:**
> From the lsblk output,which partitions do you expect to see?
The encrypted partitions need to be "opened" before any file system inside can be seen or accessed.

Past behavior was the block devices, hard files,   were shown in the "On This Computer" section of the "Other Locations". However I couldn't access an encrypted device until I entered the passphrase after clicking on that block device. 

The USB drives sdb and sdh had been automatically shown as mounted on the left pane of the files window.

---

### Post by dwarthog on 2021-06-02
Finally found what was wrong but I've no idea how this issue occurred. 

I finally looked in my system logs and found that there was an error message associated with fd0 which indicated it was a floppy drive. There is not a floppy drive on this system. 

I checked  my bios settings and it  had a floppy drive option selected which I disabled. I've no idea how this was enabled or if it had always been like this. 

Now all my block devices show up correctly in Files -> Other Locations -> On this Computer section. 

Hopefully this is helpful to someone else along the way.

---

