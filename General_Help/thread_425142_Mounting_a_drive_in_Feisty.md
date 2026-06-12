---
title: "Mounting a drive in Feisty"
date: 2007-04-27
forum: General Help
---

### Post by geovino on 2007-04-27
Now that I have Feisty installed I thought that it automatically mounted all drives, it does as a live cd. 

My old windows partition that I wanted to copy some music files from tells me:
You are not privileged to mount this volume. Why how do I change this?  Ubuntu is on hda2 and windows is hda1.

What line do I have to add to what file? 

Thanks

---

### Post by leg on 2007-04-27
You can add it to the file /etc/fstab to have it mount at boot time. Look at that file and you should see how to do it. You will need the right file system installed to read it though and there may be problems if you want to write to a NTFS drive.

---

### Post by Rospo Zoppo on 2007-04-27
Please post here the output of ```
fdisk -l | grep NTFS
``` and ```
cat /etc/fstab
```

---

### Post by binarybird on 2007-04-27
geovino - 

surprised that Feisty did not already detect your WinX partition in the fstab table. 

several ways to go at this you need to look at your fstab file to see what's in there now... from a console prompt enter:

$** less /etc/fstab**

It should vomit out something similar to my example below (a test box of mine) ->

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=<some big number>    /   ext3    defaults,errors=remount-ro   0       1
# /dev/hda2
UUID=<some big number>   /boot           ext3    defaults        0       2
# /dev/hda1
UUID=<some big number> /windows     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=<some big number none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


You need to know which partition (read dev) you set your windows partition to when you were installing. If you don't remember you can do a quick check by entering:

$ **fdisk -l -u /dev/xxx** (where xxx is your device type, in mytest box it happens to be hda)

This will print out your partition table. Look for the line that has HPFS/NTFS in the "System" column. Note the device it is on. Example: **/dev/hda4**

Use the above example to code in your windows partition. You'll notice I set mine to mount to /windows. I created that folder on the root filestructure. You can set it to whatever you want, just make sure the folder exists and that root owns it. I believe the default for Ubuntu is to throw it under /media/xxx. 

Not sure what the direction was there's multiple opinions on this, but Ubuntu now uses UUID instead of just the device label. If you are not sure what the UUID is do the following:

Take the device location that you found from "fdisk -l" command and enter at the prompt:

$ **vol_id -u /dev/xxx**

That will hit you back with the UUID of the device. 

Hope that helps...happy computing :)

---

### Post by geovino on 2007-04-27
davek@davek-desktop:~$ fdisk -l | grep NTFS
davek@davek-desktop:~$ 
davek@davek-desktop:~$ 
davek@davek-desktop:~$ 

davek@davek-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a3c769bc-bc62-4875-adbc-b71b1e898ff0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c6d7b041-d40b-46a3-873b-6b1fde8e571f none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1 /media/windows ntfs nls=utf8,umask=0222 0   0davek@davek-desktop:~$

---

### Post by lw5 on 2007-04-27
Doesn't look like windows is on hda1 (it's actually **s**da1 in Feisty), cause it says it is an ext3 (=linux) partition. The drive you're looking for is /dev/sdb1 (are you aware that windows and ubuntu aren't actually on the same fysical disk?) So maybe this info helps..

Else, if you want (or have) to change your windows fstab line, check [_this_](https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28mount%29)

---

### Post by binarybird on 2007-04-27
> **lw5 said:**
> Doesn't look like windows is on hda1 (it's actually **s**da1 in Feisty), cause it says it is an ext3 (=linux) partition. 

The hda I used was for reference as an example, not telling him that was what his disk was. Not sure what you are trying to tell him that just because it has an **s**  that it is Feisty (that has nothing to do with it being Feisty) and ext3 that it equals linux. Read the full post. 

The h and s refer to drive type to the kernel. IDE, SCSI, SATA etc.

---

### Post by geovino on 2007-04-27
Sorry for the confusion, I gave you info from this pc when its on my other older pc that has WinXP on hda1 and Ubuntu is hda2 and PCLOS is on a separate hd that's hdb1
This pc has access to the winxp drive. I'll have to do those commands from the other pc.

---

### Post by geovino on 2007-04-27
Here's the commands from the PC I want to get access to winxp drive:

davek@davek-desktop:~$ fdisk -l | grep NTFS
davek@davek-desktop:~$ 
davek@davek-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=78fa238b-c3ae-4485-87ce-e97adf596f35 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=59c0a165-8b01-4d05-8075-f47ebe9a252e none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1   /mnt/win   ntfs   nls=utf8,umask=0222   0   0
davek@davek-desktop:~$

---

### Post by lw5 on 2007-04-28
> **binarybird said:**
> The hda I used was for reference as an example, not telling him that was what his disk was. Not sure what you are trying to tell him that just because it has an **s**  that it is Feisty (that has nothing to do with it being Feisty) and ext3 that it equals linux. Read the full post. 

The h and s refer to drive type to the kernel. IDE, SCSI, SATA etc.

Instead of saying I should read the full post, perhaps you should look somewhat better at the thread.
I wasn't referring to your post at all.
And in Feisty - this is actually because/dependent on the kernel version - IDE drives ARE reffered to as sdx instead of hdx (there are a lot of people having trouble with the fstab setup because of this).

@TS;
I'm sorry, I gave you the wrong link before, I meant to give you [_this one_](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

I'm a bit confused as your Windows partition should already be mounted, so why do you get a 'You are not privileged to mount this volume'?

What happens if your replace (rather, outcomment it)  this:
/dev/hda1 /mnt/win ntfs nls=utf8,umask=0222 0 0

with this:
/dev/hda1 /mnt/win ntfs  ro,auto,user,fmask=0111,dmask=0000 0 0

in your /etc/fstab file.

---

### Post by geovino on 2007-05-04
I changed the fstab but it made things worse.

---

### Post by geovino on 2007-05-04
> **lw5 said:**
> Instead of saying I should read the full post, perhaps you should look somewhat better at the thread.
I wasn't referring to your post at all.
And in Feisty - this is actually because/dependent on the kernel version - IDE drives ARE reffered to as sdx instead of hdx (there are a lot of people having trouble with the fstab setup because of this).

@TS;
I'm sorry, I gave you the wrong link before, I meant to give you [_this one_](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

I'm a bit confused as your Windows partition should already be mounted, so why do you get a 'You are not privileged to mount this volume'?

What happens if your replace (rather, outcomment it)  this:
/dev/hda1 /mnt/win ntfs nls=utf8,umask=0222 0 0

with this:
/dev/hda1 /mnt/win ntfs  ro,auto,user,fmask=0111,dmask=0000 0 0

in your /etc/fstab file.

I added the 

/dev/hda1 /mnt/win ntfs  ro,auto,user,fmask=0111,dmask=0000 0 0
line but it made it worse. so I took it of the left it as it was.

I don't know why it can't mount what ever drives and partitions I have! That was one of the good changes in Feisty, but for some reason I can't mount the drvies. 

What else can I do to solve this problem?

---

### Post by geovino on 2007-05-06
> **binarybird said:**
> geovino - 

surprised that Feisty did not already detect your WinX partition in the fstab table. 

several ways to go at this you need to look at your fstab file to see what's in there now... from a console prompt enter:

$** less /etc/fstab**

It should vomit out something similar to my example below (a test box of mine) ->

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=<some big number>    /   ext3    defaults,errors=remount-ro   0       1
# /dev/hda2
UUID=<some big number>   /boot           ext3    defaults        0       2
# /dev/hda1
UUID=<some big number> /windows     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=<some big number none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


You need to know which partition (read dev) you set your windows partition to when you were installing. If you don't remember you can do a quick check by entering:

$ **fdisk -l -u /dev/xxx** (where xxx is your device type, in mytest box it happens to be hda)

This will print out your partition table. Look for the line that has HPFS/NTFS in the "System" column. Note the device it is on. Example: **/dev/hda4**

Use the above example to code in your windows partition. You'll notice I set mine to mount to /windows. I created that folder on the root filestructure. You can set it to whatever you want, just make sure the folder exists and that root owns it. I believe the default for Ubuntu is to throw it under /media/xxx. 

Not sure what the direction was there's multiple opinions on this, but Ubuntu now uses UUID instead of just the device label. If you are not sure what the UUID is do the following:

Take the device location that you found from "fdisk -l" command and enter at the prompt:

$ **vol_id -u /dev/xxx**

That will hit you back with the UUID of the device. 

Hope that helps...happy computing :)

Here's my info from the command:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=78fa238b-c3ae-4485-87ce-e97adf596f35 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda5
UUID=59c0a165-8b01-4d05-8075-f47ebe9a252e none            swap    sw            
  0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1   /mnt/win   ntfs   nls=utf8,umask=0222   0   0


What should I add to the fstab? 
WinXP : hda1
Ubuntu: hda2
PCLOS: hdb1

It's odd that this happened with Feisty. You could mount all the drives and partitions from the Live CD!

---

