---
title: "Has the root user got a disk usage limit?"
date: 2008-05-25
forum: General Help
---

### Post by mrund on 2008-05-25
I'm phasing out my WinXP use entirely, and so the other night I moved most of my data from the XP partition to the Ubuntu partition. Plenty of room there: tens of gigabytes left after the move. But suddenly I start getting error messages that suggest that I have hit some kind of ceiling in my disk usage. Hey, I'm the fricking' root!? Has the root user got a disk usage limit? How do I raise this limit?

---

### Post by Monicker on 2008-05-25
There is no default limit on disk space usage by root.  In fact there are times when only root can log in when disk space is low, because there is always a "reserve" allocated especially for root.

What exactly are the error messages your are receiving?  

Post the output of these commands:
```

df -h
sudo du -ch --max-depth=1 /
```

---

### Post by mrund on 2008-05-26
I've found out that it's not just my account, my wife's got problems too.

martin@livingroom-desktop:~$ df -h
Filsystem            Storlek Anvnt Tillg Anv% Monterat på
/dev/sda3              11G  9,8G     0 100% /
varrun                125M  100K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   68K  125M   1% /dev
devshm                125M   12K  125M   1% /dev/shm
lrm                   125M   38M   88M  30% /lib/modules/2.6.24-16-generic/volatile
/dev/sda1              32M  6,2M   26M  20% /media/sda1
/dev/sda2              45G   33G   13G  73% /media/sda2
/dev/sdb1             201G   36G  166G  18% /media/sdb1
/dev/sdb2              31G  2,1G   28G   7% /media/sdb2
overflow              1,0M   20K 1004K   2% /tmp

martin@livingroom-desktop:~$ sudo du -ch --max-depth=1 /
[sudo] password for martin: 
4,0K	/initrd
92K	/dev
5,2M	/bin
16K	/lost+found
13M	/etc
6,5M	/sbin

The main error message I'm getting is about OpenOffice being unable to save work because of "insufficient disk space". Also, Firefox is acting strange, being unable to load the bookmark toolbar.

---

### Post by forestpixie on 2008-05-26
> Has the root user got a disk usage limit?Only when you hit 100% :)

your root is full - apart from the space it keeps for just such a time.

You can try and clean out the apt cache - will give you probably enough room to manoeuvre 

```
sudo apt-get clean
``` If you can't boot - then run the command from recovery mode. Then you'll need to do a bit of housework in there - I assume your /home is not seperate.

---

### Post by forestpixie on 2008-05-26
Ok - managed to post the same thing again:)

---

### Post by mrund on 2008-05-26
Oh, silly me. I've gotten my various disk partitions mixed up. (Partly because I don't know how to give them descriptive names.) Yes, my root partition is full to the brim. Thanks!

---

### Post by forestpixie on 2008-05-26
I've changed names withthis in the past - changing partitions to suit obviously :)

```
sudo tune2fs -L NewLabelName /dev/sda1
```

---

### Post by mrund on 2008-05-27
Thanks, I'll try that.

But now I have a new problem.

After a botched original attempt to install Ubuntu on my second hard disk, I had an inactive linux partition sitting around on that disk, and that was what confused me regarding the disk space issue. So last night I deleted that partition with GParted.

Now, every time I boot Ubuntu, I get a string of error messages, apparently because the OS is for some reason upset that the unused partition is gone from the second disk. Then it dumps me at the prompt and instructs me to press CTRL-D if I want to resume the booting process. I press CTRL-D, and everything works normal.

Why does Ubuntu complain about an unused partition disappearing? How do I get rid of this unnecessary step in the boot process?

---

### Post by forestpixie on 2008-05-27
I'd expect that it was on the fstab for mounting - edit the file and remove or # out the lines with the dead partitions. As an aside if you resize to take up the unallocated space the UUID will chnage and you'll get the same problem.

```
gksudo gedit /etc/fstab
```

---

### Post by mrund on 2008-05-27
An attempt to rename my WinXP partition with tune2fs just gave me an error message, "Bad magic number in super-block".

---

### Post by forestpixie on 2008-05-27
Probably - > tune2fs - adjust tunable filesystem parameters on ext2/ext3 filesystems
:)

You should be able to change ntfs with a different program - here's the page it's on
 [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by mrund on 2008-05-29
> if you resize to take up the unallocated space the UUID will change and you'll get the same problem.

Interesting. So how would I go about resizing to avoid the problem?

---

### Post by forestpixie on 2008-05-29
UUIDs change when a partition is changed - as far as I can tell there is nothing you can do about it. It is fairly simple to change the fstab line - if you know you've changed sda1 for instance you can get the new UUID by running sudo blkid.

Open the fstab for editing and chnage the line for sda1 to suit the new UUID, alternatively don't use the UUID and use /dev/sda1 instead.

If it causes problems at boot you can edit fstab at the root prompt in recovery mode.

---

