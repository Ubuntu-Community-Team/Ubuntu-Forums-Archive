---
title: "Save home backup to windows disk ?"
date: 2018-07-24
forum: General Help
---

### Post by verenard on 2018-07-24
Hi guys, my issue is this -

I have ubuntu 16.04
I want to upgrade to 18.04
I want to back up my home folder just in case
I have a second disk with windows on it and enough room for my home folder
Can I back up to my windows disk ?
How do I sort out needed permissions etc ?

thanks

---

### Post by yancek on 2018-07-24
When you say 'windows disk', do you mean another drive on which you have an install of some version of windows or just a secondary backup drive formatted ntfs?  I guess  in either case, you should shrink the windows partition from windows with Disk Management, run chkdsk from windows then create a partition with a Linux filesystem on it on which you can copy your data.  I would suggest you check out the link below which offers several methods of copying or doing a backup.  I would hesitate to do it to an ntfs partition but perhaps someone else with more knowledge of windows will have a suggestion for you.

[https://askubuntu.com/questions/225865/copy-files-without-losing-file-folder-permissions](https://askubuntu.com/questions/225865/copy-files-without-losing-file-folder-permissions)

---

### Post by verenard on 2018-07-24
Hi yeah it's a second disk with a win10 install. Can I shrink it from within windows like you said ? If I can shrink it with gparted, and make a back up partition without screwing up my win10 that would be ok. Thanks.

---

### Post by ajgreeny on 2018-07-24
You should **always use Windows own disk management system to shrink a Windows partition**; using gparted could make the windows unbootable without first running a repair.

---

### Post by verenard on 2018-07-24
Ah thanks. I can do this from within the same OS I am shrinking ?

---

### Post by dragonfly41 on 2018-07-24
When setting up my dual boot and adding an ntfs SHARE partition between Windows 10 and Ubuntu
(to share files between Windows and Ubuntu) I remember I took advice to first create a 
Windows recovery USB as a precaution.

---

### Post by oldfred on 2018-07-24
The reason not to backup Linux to NTFS or other Windows formats is that they do not support Linux ownership & permissions. So then you lose those.

If just your data and no Linux system files, you probably can just reset your data to the defaults used by /home. But never copy any other system folder to NTFS.

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by verenard on 2018-07-24
Thanks for the links.
Yeah I want to keep things like documents, pics, mozilla profiles, data. 

Actually I don't know what a system file is, I assume it's things like configs and executables ?

So things like repository data, I would save them and then just copy paste them into the new installation ?

You know, I'd like to just go ahead and do-release upgrade and not think about any of this.... but I'm no stranger to data disaster, and I need to learn how to back up anyway. Ever had a hard drive fail just when the tax man wants your records ? 
It's not fun.

---

### Post by verenard on 2018-07-24
I've been reading tips that say super defrag windows first to collate all the data in one chunk before resizing a partition. Also delete hibernation and page files.

---

### Post by dragonfly41 on 2018-07-24
Why not just find an unused external drive to place in a USB container, format for Ubuntu only, and use that as your backup.

If possible, keep Windows and Ubuntu in separate homes.

---

### Post by verenard on 2018-07-24
I have another ubuntu drive but I think there's something wrong with it. I tried copy pasting my home folder to it but it wouldn't go, there was some problem I can't recall now. Maybe a permission error. I want to keep it in another rig anyway.

---

### Post by verenard on 2018-07-24
Money. And my spare drives are in other boxes. I tried another ubuntu disk but I couldn't copy/paste my home folder to it without errors. 
Edit - it stops with 

"The folder &#8220;.gvfs&#8221; cannot be handled because you do not have permissions to read it."

So maybe there is stuff in my home folder that I can't shift anyway because it's from another machine and I don't have ownership ?

I think I will experiment with trying to just move essential stuff rather than the whole lot. I'd rather move the whole lot.

---

### Post by yancek on 2018-07-24
I'm not sure where you are based on your last posts but, if you want to shrink a windows partition then first run Disk Defragmenter.  When that finishes, use Disk Management in windows to shrink the partition.  When that finishes, reboot and run chkdsk from windows until it shows no errors then create the Linux partition and format it.

---

### Post by oldfred on 2018-07-24
I have seen where you need to exclude .gvfs in backups.

 sudo rsync -aXS --exclude='/*/.gvfs' /home/. /media/home/.

But I exclude many others also:
[https://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](https://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

---

### Post by verenard on 2018-07-25
Well, I just mad a new folder on the windows drive, ran nautilus as super user and managed to copy my home folder into it.. I had to skip a few files, like .gvfs but I got my essentials over. I'm hoping that I don't need to mess around with permissions if I have to actually use the back up I made. I probably could have deleted a lot of cruft and unused apps first to save time but there you go, I got it. Thanks for the help. Now I have to just do-release.

---

### Post by btindie on 2018-07-25
Alternatively, to preserve the ownership and permissions correctly you could have created a large file on the windows NTFS partition and formatted that with ext4 then mounted it via a loop device. That way it'd be no different to any other Linux partition.

You'll need to know where you're windows partition is mounted, in the below it's /media/windows

```

# create a large file 20G in size
dd if=/dev/zero of=/media/windows/ext4.img bs=1 count=0 seek=20G

# create an ext4 filesystem on it
mkfs.ext4 -m0 /media/windows/ext4.img

# mount it making it accessible via /mnt
sudo mount -o loop /media/windows/ext4.img /mnt/

```

You'd then be able to use the rsync copy to copy all files preserving permissions to the disk image. Adjust the size of the created disk image to suit your needs.

Then
```
sudo umount /mnt
```
when you're done to unmount the disk image.

---

### Post by verenard on 2018-07-25
Thanks that's cool I could use that in future.
For now, though, the upgrade went fine with no data loss. And ubuntu 18.04 seems like an improvement to me. In fact right away it solved a scaling problem with my HDMI monitor and AMD card. I'm impressed.

---

