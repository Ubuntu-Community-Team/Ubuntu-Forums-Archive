---
title: "NTFS read/write (live CD)"
date: 2007-09-04
forum: General Help
---

### Post by Packrat1947 on 2007-09-04
Excuse me if this has been answered before.

I just booted off the newest ubuntu, and was pleased to see that my SATA drive is seen.  This is a HP 6000 dv lappy.  Now, how can I get full read/write privileges to my drive?

This is using the live CD - as an emergency boot CD.  Is there something like a 'cheat code' or something.  

I tried giving myself permissions, but everything was greyed out.

Thanks for you help.

Packrat1947

---

### Post by the_it on 2007-09-04
What you are trying to do is to read and write yourfiles that are in the drive, not touch the drive itself.

The solution for full ntfs read-write is to install a program called ntfs-config.  It should be as simple as
```
sudo apt-get install ntfs-3g ntfs-config
```
then you can run ntfs-config to enable write support to your ntfs partition.
```
sudo ntfs-config
```
and tell it to enable write support to your internal ntfs drive.  I am currently not sure if it tries to remount all ntfs drives by itself, but I think it should.  Try writing to it first to see if you can.  If you can't, you have to manually remount the drive.  If your ntfs partition is /dev/sda1, the following command should do it
```
sudo umount /dev/sda1
sudo mount -t ntfs-3g /dev/sda1 /mnt
```
 in the above, /dev/sda1 is the device file of your drive.  You can find out what device file your drive is by typing 
```
mount |grep sda
```
in the terminal and taking note of which device entry (/dev/something)  corresponds to the folder location of the drive you're clicking on.
/mnt is the location where you want to mount it.  If you did the *mount |grep sda* above, you can replace /mnt with the folder location (/dev/something on /media/foldersomething) you see.

The problem with your situation is that you are running from a livecd.  It's possible to use apt-get on a livecd to install software, however, all your changes will be running on memory only.  Which means that if you run out of ram on your system, things won't work well.

Hope this helps.

---

### Post by Packrat1947 on 2007-09-06
Hello,
Thanks for the considerable reply.  

However, we DO need true read/write access to ntfs.  Many  times we need to open the System Volume Information, - rename the five hives, and copy them to the C:\Windows\System\Config folder.  This is common in Windows repair.

I'll try your suggestions and will see what I can come up with.  I already use miniPE, Barts, and ERD, but I'm always looking for more 'safety nets'.   So true read/write is VERY important in data recovery.   We want to get the system back running, not just copy files.

Right now, Vista is struggling.  This is the time for Linux to make deep inroads in the OS competition.  The window of opportunity is brief.   I see that Knoppix has an icon on the Desktop to activate ntfs writing.  All distro's should have this.

Thanks,
Ron N.

---

### Post by strabes on 2007-09-06
NTFS is proprietary and therefore is not included by default in ubuntu. I suspect that there will eventually be an "easier" way to enable this, just like there is an "easier" way to install various restricted drivers. (as if installing ntfs-3g and ntfs-config weren't easy enough)

---

