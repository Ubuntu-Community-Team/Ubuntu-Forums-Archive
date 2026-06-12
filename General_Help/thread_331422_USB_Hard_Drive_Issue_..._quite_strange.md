---
title: "USB Hard Drive Issue ... quite strange"
date: 2007-01-04
forum: General Help
---

### Post by Ciego on 2007-01-04
I am having a very strange issue with my USB hard drive and I believe that it is time to stop trying to fix it on my own.  ](*,) 

Here is the situation ... I have a USB hard drive (WD My Book series 160GB) that I have been using with Ubuntu for 6 months with no issues.  I plugged it in, it mounted, I have saved to it, etc ... everything was working fine.  I had even unplugged it a few times to use with a Windows PC (not mine, I am Windows clean as of May 2006 :-D ) and with my PS3 and then plugged it back into my Ubuntu machine and still everything was fine.  

Well ... I recently unplugged it from my Ubuntu machine, plugged it into a Windows machine, transfered some files, and then plugged it back into my Ubuntu machine.  Then the problems started.  The drive mounted and showed up on my desktop, and I can access the drive if I use the "root-nautilus here" script on it, but when I click on the icon on my desktop, the nautilus window opens and nothing shows up in the window.  The window then freezes and I have to force quit.  

I tried to change the permissions but that did not seem to work.  I tried unmounting and remounting but that didn't seem to work.  I searched through countless threads but I can not find any similar issues to this one.  If you have any advice, please respond.  

On a comical note ... I thought that I would never again have to deal with Windows screwing up my machine ... I guess I was wrong. 

Here is some info that may help to diagnose my problem.  Let me know if you would like more

```
Me@My-desktop:~$ fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    c  W95 FAT32 (LBA)
```
Doesn't this look a little odd?  I don't even see my primary hard drive here.

```
Me@My-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=5e47357c-db26-4087-864a-38287e6eef0d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=4083b25d-21f9-4f20-9a3b-5e43c201e013 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
This also looks wierd to me ... why is my main hard drive commented out?

```
Me@My-desktop:~$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sda1 /media/My\040Book vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/hdc /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=jblind 0 0
jblind@jblind-desktop:~$ 
```

Thank you in advance for your time and assistance.

---

### Post by jackocleebrown on 2007-01-14
Hi Ciego,

I can't help you much but I can answer a couple of your worries.

if you do "sudo fdisk -l" you'll see your other drives, I noticed this the other day.

In your fstab file your main hard disks are not commented out it is just that they are defined using the partition UID (unique identifiers) instead of the hardware paths (e.g. dev/hda1). The commented hardware paths are put there automatically by the installer to make it easier to identify what the line below is referring to.

Sorry I can't help more, hope you get a better answer soon!

Jack.

---

### Post by dcstar on 2007-01-14
> **Ciego said:**
> 
.......
Well ... I recently unplugged it from my Ubuntu machine, plugged it into a Windows machine, transfered some files, and then plugged it back into my Ubuntu machine.  Then the problems started.  The drive mounted and showed up on my desktop, and I can access the drive if I use the "root-nautilus here" script on it, but when I click on the icon on my desktop, the nautilus window opens and nothing shows up in the window.  The window then freezes and I have to force quit.  
.......

There may be some directory corruption that Ubuntu cannot handle.

Copy all of the files off the stick on your Windows PC and then re-format the drive and copy them back, then see if Ubuntu can now mount the drive.

---

### Post by dcstar on 2007-01-14
> **Ciego said:**
> 
.......
/dev/sda1 /media/**My\040Book** vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
......

Actually, on a second look that Disk Label looks very suspicious, I am not sure that Ubuntu can use something with an encoded "\" character.

You may try renaming the drive in Windows (maybe to "My-Book"?) and see if things change.

---

### Post by Ciego on 2007-01-15
> **dcstar said:**
> There may be some directory corruption that Ubuntu cannot handle.

Copy all of the files off the stick on your Windows PC and then re-format the drive and copy them back, then see if Ubuntu can now mount the drive.

My external hard drive has about 80GB on it right now and the only other hard drive I have at the moment is 40GB but I will surely try that when I get a larger hard drive.

> **dcstar said:**
> Actually, on a second look that Disk Label looks very suspicious, I am not sure that Ubuntu can use something with an encoded "\" character.

You may try renaming the drive in Windows (maybe to "My-Book"?) and see if things change.

The reason for this is that the drive itself has a label of "My Book" and Ubuntu sees this as "My\ Book"  I have tried changing that label and I took all of the autorun files off of the drive.  I managed to get the permissions to change somehow, but not to the ones that I wanted. ](*,)  

I think that backing it up and reformatting sounds like a good idea.  If that works, I sure won't plug it back into a Windows machine again.  I will just have to connect it to my server and make it available to the windows users in the house.  (That is actually what I was trying to do when I noticed it was messed up)

Thanks for the advice.

---

