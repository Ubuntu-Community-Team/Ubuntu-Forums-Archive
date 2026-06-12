---
title: "External harddrive not detected"
date: 2007-12-13
forum: General Help
---

### Post by petitevache on 2007-12-13
I'm on Ubuntu and my computer doesn't detect my external hard drive (I want to get files off my computer onto it.) Does anyone know how to fix this?

---

### Post by atlfalcons866 on 2007-12-13
what file system is it? Is it NTFS?

If it is NTFS go here [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

---

### Post by petitevache on 2007-12-13
I'm trying to follow the steps, but when I try to install the ntsf-config package (with the code: sudo apt-get install ntfs-config) I get an error message saying "Couldn't find package ntfs-config". :/

---

### Post by viking777 on 2007-12-13
> **petitevache said:**
> I'm on Ubuntu and my computer doesn't detect my external hard drive (I want to get files off my computer onto it.) Does anyone know how to fix this?

Do you really mean that it isn't being detected or that you are not seeing it as detected? They are very different things.

Unplug your hard drive then open a terminal and run the command

```
sudo udevmonitor
```

When that is running plug in the drive and see what happens. If it is not detected you will not get any response, if it is detected you will get  a lot of info on screen the last line of which will contain its address, in my case this reads

```
UDEV  [1197560025.420098] add      /block/sdb/sdb1 (block)
```

Which means my device is located at /dev/sdb1. All you have to do then is mount it.

Control/c will exit udevmonitor.

---

### Post by petitevache on 2007-12-13
Oh, wow : ) You were right, it worked. My address is almost the same as yours... so now how do I mount it?

---

### Post by viking777 on 2007-12-13
You search the forum for the answer to that, it has been written about 1000 times before.

---

### Post by strabes on 2007-12-13
> **petitevache said:**
> Oh, wow : ) You were right, it worked. My address is almost the same as yours... so now how do I mount it?

Before asking questions like this you should probably search the forums/internet. But here is what you need to do to mount it manually. I don't know why it's not mounting automagically; pretty much everything gets automagically mounted now.

```
sudo mkdir /media/externaldrive
sudo mount /dev/sdb1 /media/externaldrive
```

---

### Post by petitevache on 2007-12-13
Thank you. I did search the forums, I still am, but whatever I do it doesn't work. I'm probably doing something wrong or there's something I should know that's blatantly obvious to everyone else, I don't know... gah. 

I typed in the command you said and it gave me:

mount: you must specify the filesystem type

---

### Post by petitevache on 2007-12-13
Browsing the forums still, tried this code:

sudo mkdir /media/sdb1
sudo mount -t ntfs /dev/sdb1 /media/sdb1 -o nls=utf8,umask=0222

and I got: 

NTFS signature is missing.
Failed to mount 'dev/sdb1': Invalid argument 
The device 'dev/sdb1' doesn't have a valid NTFS
Maybe you selecred the wrong device? Or the whole disk instead of a partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around? 

Sigh. :/

---

### Post by vanadium on 2007-12-13
This surprises me because the mount command is usually smart enough to recognize the file system automatically. To make sure what the name of your external drive is and how Ubuntu recognizes it, post the output here of following commands (with your hard drive powered on and connected):

sudo fdisk -l
mount

(-l in the first command is the l of "list", not 1)

---

### Post by petitevache on 2007-12-13
After sudo fdisk -l I get: 

Disk dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders  of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59271f32

Device  Boot            Start                 End                      Blocks               Id            System
/dev/sda1   *                 1                9728                 8140128+              7           PFS/NTFS

Disk /dev/sdb: 250.0GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders  of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeef844d8

Device  Boot            Start                 End                      Blocks               Id            System
/dev/sdb1   *                 1              30401              244196001              c           W95 FAT32 (LBA)



After I type the code mount, I get: 

proc on /proc type (rw)
sysfs on/sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
undev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev.pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other, blksize=4096)

---

### Post by vanadium on 2007-12-13
I do not quite understand your output: there is no linux formatted partition mentionned, and root   is not listed. That aside, your sda1 is  80 GB and nfts, your sdb1 250 GB is FAT32. Probably, your sdb1 is your external drive that you do not see, because sda1 is available in /media/disk.

Execute  now the following command and post any output here: it will tell us if sdb1 can mount, and if it cannot, why.

sudo mkdir test
sudo mount -t vfat /dev/sdb1 test

No output will result if the disk is well mounted. If there is a problem, the output will give us a clue, so post it here. Is your external drive a USB drive?

---

### Post by petitevache on 2007-12-13
Yes, it's a USB drive. 

I typed the command in and it gave no output. Just to make sure I tried again and I got: "mount: special device /dev/sdb1 does not exist" 

...

---

### Post by vanadium on 2007-12-13
You'd better post your output here. I cannot see whether you typed a mistake when entering the command a second time (e.g. omitting the starting slash). After performing the command and it does not give an error, check again the output of "mount". Also check whether you can see the contents of the drive with the command

ls -l test

To unmount the drive, use

sudo umount test

or

sudo /dev/sdb1

---

### Post by petitevache on 2007-12-13
Yes, I can see the contents with the "ls -l test" code.

Also, when I type the "sudo mount -t vfat /dev/sdb1 test" command, I get: 

mount: /dev/sdb1 already mounted or test busy
mount: according to mtab, /dev/sdb1 is mounted on home/ubuntu/test


*edit* When I go into Home on ubuntu, there's a file called "sbd1" but it's empty.

---

### Post by vanadium on 2007-12-13
This shows that your drive can mount correctly. The error is not in your disk. Now unmount it again with the umount command as explained above.

The issue seems now: why doesn't it automount when you plug it in. There is not much I will be able to help you in that area, only: make sure that automounting is enabled in System - Preferences - Removable drives and media. On the Storage tab, "Mount removable drives when hot-plugged" should be checked.

---

### Post by petitevache on 2007-12-13
Automounting is enabled, the box is checked... sigh. Thanks for all your help. 

Would unmounting get rid of the sdb1 folder in Home? Because I unmoounted and it's still there and just wondering if I did something wrong again. 

By any chance would you know why, when I plug in an mp3 player and try to copy files onto it, it tells me that I have no permission to do this? (it worked a couple times and then suddenly I started getting that error)

---

### Post by vanadium on 2007-12-13
What ubuntu version are you using? An usb should automatically mount. Perhaps it is your particular model that is a bit problematic. Unless a solution comes up, you will need to mount/unmount it manually. There is one last chance and that is that the fat file system is not OK (I am not sure because I would expect it not to mount manually neither). So try to check the volume and post the output here. First unmount the disk if it is still mounted (check with "mount" if it is mounted, if mounted then unmount with "sudo umount /dev/sdb1" as outlined before. Then check the volume:

sudo dosfsck /dev/sdb1

Again, post the output here.

---

### Post by petitevache on 2007-12-13
I downloaded Ubuntu a few days ago, I think it's the latest version, 7.10? 

After I typed in sudo dosfsck /dev/sdb1, I got: 

dosfsck 2.11, 12 Mar 2005, FAT32 LFN
open /dev/sdb1:No such file or directory

---

### Post by petitevache on 2007-12-13
If I install ubuntu directly to my computer, can I then burn files onto a CD? That might be faster and easier than trying to figure all this out.

---

### Post by vanadium on 2007-12-13
This looks as if your computer does not see /dev/sdb1 anymore. Does it still appear in the output of "sudo fdisk -l"?

---

### Post by petitevache on 2007-12-13
Oh, sorry - I think someone from my family plugged out the hard drive by accident. 

After the code sudo dosfsck /dev/sdb1, I get:

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup. 
Differences: (offset:original/backup)
65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
?

---

### Post by vanadium on 2007-12-13
The disk has errors. It will probably mount properly when the errors are fixed. I guess you need to give an option for dosfsck to effectively correct. Run the command

sudo dosfsck -a /dev/sdb1

and when the question appears, select 1 (I do not know what is the best here, but it probably won hurt).

After that, run the command a few times until the output is the same each time (giving no errors anymore). This just does automatic reparation on the file system itself (if needed). Chances are that at the end, you will find new files in the root directory of that drive with strange names: these are data in unallocated clusters (remains of inproperly closed files) and can be deleted: you will gain the disk space again.

Do the same for your mp3 player: chances are high that your issues are also caused by errors in the file system.

To prevent such errors from occurring, always properly unmount a drive/mp3 player before unplugging it.

---

### Post by petitevache on 2007-12-13
When I try the sudo dosfsck -a /dev/sdb1 command, I don't get any options to choose but:

dosfsck 2.11, Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset: original/backup)
65:01/00
Not automatically fixing this
No FSINFO sector
Not automatically creating it
/dev/sdb1: 6113 files, 7247287/7629261 clusters


If I were to do this for my mp3, how would the code change?

---

### Post by vanadium on 2007-12-14
The man dosfsck command provides information on how to run the command. For correcting your specific error, you apparently cannot use the -automatic option. This thread already provided information on how to identify a device name.

---

### Post by viking777 on 2007-12-14
Your fdisk -l output does not show any Linux partitions. Does that mean you are running Ubuntu from a live cd? If so it would have been a good idea to say that. Live cd's don't always behave the same as an installed OS. I personally have never tried detecting plug in usb devices with a live cd so I don't know how successful it is.

Anyway, as you obviously have windows and your problem seems to be with a windows file system I think it would be better in this instance to try and fix it through windows, so I suggest you boot windows and run scandisk on your external drive with 'fix errors' selected. Then try again with ubuntu.

---

### Post by petitevache on 2007-12-14
Viking777, I can't boot Windows - that's my whole problem. It won't start so I'm trying to get my files off before I reinstall.

---

### Post by vanadium on 2007-12-16
Perhaps use the -r option, for interactive:

sudo dosfsck -r /dev/sdb1

On the question "There are differences between boot sector and its backup.", answer "1". After that, answer questions by accepting the defaults. Run the command again: if all inconsistencies are fixed, no prompts will appear anymore. After that, your partition should be mounted automatically upon reboot.

---

### Post by 1jackjack on 2008-03-17
I know it's 3 months later, but I had the same problem, and this last post fixed it.
Thanks very much!
Jack

---

