---
title: "Target filesystem doesn't have requested /sbin/init"
date: 2019-04-07
forum: General Help
---

### Post by smithon2 on 2019-04-07
Turned the computer off but now it won't load and it is showing this messgae.  Have live cd but it is of later version. Running ubuntu as a partitionwith windows xp need to get files off the ubuntu any advice how to fix it so I can access my old ubuntu?

---

### Post by Rubi1200 on 2019-04-07
Hi and welcome to the forums :-)

Boot the liveCD and then follow the instructions to create a boot info summary report (see link in my signature).

Post the results here so we can try and help further.

Thanks.

---

### Post by Impavidus on 2019-04-07
Do didn't specify the versions of the installed Ubuntu and of the live disk, but in any case you can access the files on your installed Ubuntu using the live disk. The next question is whether you want to fix your installed Ubuntu or want to replace it with the newer.

---

### Post by smithon2 on 2019-04-13
> **Impavidus said:**
> Do didn't specify the versions of the installed Ubuntu and of the live disk, but in any case you can access the files on your installed Ubuntu using the live disk. The next question is whether you want to fix your installed Ubuntu or want to replace it with the newer.

As long as I can recover my old files I don't care. The version is 13 or 14 I think the live CD is the latest. How do I recover my old files? I tried this command 

udisksctl mount -b/dev/sdxy where x was the driver letter and y the partition number but it didn't work.

---

### Post by smithon2 on 2019-04-13
I can't create a boot summary from the live cd as it is not connected to the internet.

---

### Post by Impavidus on 2019-04-13
If the installed Ubuntu system is 13 or 14 .something, it's (almost) dead and not worth fixing. The simplest way to get the files is to use the file manager on the live disk. Click the partition, with a bit of luck it will mount and you can access the files. If that doesn't work, you can try it with the mount command:```
sudo mount /dev/sdxy /media/something
```No password needed in the live session. Then you can copy the files to an external drive.

---

### Post by smithon2 on 2019-04-17
> **Impavidus said:**
> If the installed Ubuntu system is 13 or 14 .something, it's (almost) dead and not worth fixing. The simplest way to get the files is to use the file manager on the live disk. Click the partition, with a bit of luck it will mount and you can access the files. If that down't work, you can try it with the mount command:```
sudo mount /dev/sdxy /media/something
```No password needed in the live session. Then you can copy the files to an external drive.

How do I 'click the partition'? Also in the code do you mean media/something?

---

### Post by Rubi1200 on 2019-04-17
First try this from the liveCD/USB:
[https://askubuntu.com/questions/190239/how-to-access-hard-drive-files-from-livecd](https://askubuntu.com/questions/190239/how-to-access-hard-drive-files-from-livecd)

By clicking on the partition, Impavidus means that you should be able to mount the drive/partition without anything else needed done. An icon will then appear on the live desktop and you can navigate to whichever folders you need.

If it works, backup all your important files and folders before deciding on the next step.

---

### Post by smithon2 on 2019-04-23
> **Rubi1200 said:**
> First try this from the liveCD/USB:
[https://askubuntu.com/questions/190239/how-to-access-hard-drive-files-from-livecd](https://askubuntu.com/questions/190239/how-to-access-hard-drive-files-from-livecd)

By clicking on the partition, Impavidus means that you should be able to mount the drive/partition without anything else needed done. An icon will then appear on the live desktop and you can navigate to whichever folders you need.

If it works, backup all your important files and folders before deciding on the next step.

Okay thanks I have managed to access the files but it won't let me copy them onto a usb stick even though it detects the stick

---

### Post by Rubi1200 on 2019-04-23
How are you trying to copy them over, drag and drop?

What error messages, if any, do you get?

---

### Post by smithon2 on 2019-05-06
> **Rubi1200 said:**
> How are you trying to copy them over, drag and drop?

What error messages, if any, do you get?

yeah drag and drop the error message is 

Error while copying

There was an error creating the folder 'Pictures'  Error opening file '...........' No space left on device

---

### Post by Rubi1200 on 2019-05-06
Sorry if this sounds like stating the obvious, not intended like that.

1. do you have enough space on the USB or external drive for all your files and folders you want to save?

2. have you tested with just one folder first to make sure it is copying over correctly?

---

### Post by smithon2 on 2019-05-15
> **Rubi1200 said:**
> Sorry if this sounds like stating the obvious, not intended like that.

1. do you have enough space on the USB or external drive for all your files and folders you want to save?

2. have you tested with just one folder first to make sure it is copying over correctly?

There should be enough space it says there is 10gb on the flash drive and there is only 5gb to copy

No it won't even copy one file is there another way to get them off thanks?

---

### Post by oldfred on 2019-05-16
With both old system & USB flash drive mounted or seen in file browser, post these.
df -h
lsblk-f

---

### Post by smithon2 on 2019-05-18
> **oldfred said:**
> With both old system & USB flash drive mounted or seen in file browser, post these.
df -h
lsblk-f
 df -h

Filesystem        Size         Used        Avail       Use%     Mounted on
udev                1.5G         0            1.5G        0           /dev
tmpfs               300M        1.5M      298M        1           /run
/dev/sro           1.9G         1.9G      0              100       /cdrom 
/dev/loop0        1.8G         1.8G      0              100       /rofs
/cow                 1.5G         360M     1.2G         25        /
tmpfs                1.5G         0           1.5G         0         /dev/shm
tmpfs                5.0M         8K         5.0M         1         /run/lock
tmpfs                1.5G         0           1.5G         0         /sys/lfs/cgroup
tmpfs                1.5G         0           1.5G         0         /tmp
tmpfs                300M        48K       300M         1        /run/user/999
/dev/loop1         91            91           0           100
/dev/loop2         35           35            0           100
/dev/loop3         141          141          0           100
/dev/loop4         2.3M         2.3M        0           100 
/dev/loop5         13M          13M         0           100  
/dev/loop6         15M          15M         0           100
/dev/loop7         3.8           3.8           0           100

---

### Post by oldfred on 2019-05-18
You did not mount flash drive you are copying to, so it only shows your live installer.

---

### Post by smithon2 on 2019-05-20
> **oldfred said:**
> You did not mount flash drive you are copying to, so it only shows your live installer.
how do I mount it?

---

### Post by oldfred on 2019-05-20
If using file browser, you should just be able to click on it. 
Often it automounts just by plugging it in.

Were you trying to copy to the flash drive installer which is not writeable?

---

### Post by smithon2 on 2019-05-30
> **oldfred said:**
> If using file browser, you should just be able to click on it. 
Often it automounts just by plugging it in.

Were you trying to copy to the flash drive installer which is not writeable?

It's worked now it was saying there was no space left on the drive but there was. However I just wiped the flash drive and it allowed me to copy the pictures to it.

---

