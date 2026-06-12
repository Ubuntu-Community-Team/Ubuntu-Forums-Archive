---
title: "Can Ubuntu 7.10 be run without UUIDs?"
date: 2008-04-27
forum: General Help
---

### Post by taylorkh on 2008-04-27
Well it seems that those UUIDs are busting my silicons again.  Here is the situation:

My PC consists of a hard drive rack with several removable hard drives (SATA 80GB) on which I install various operating systems. I have XP, Ubuntu - Production (for which I am careful to document any changes), Ubuntu - test (which was cloned from Ubuntu - Production and which I use to test things before I install them on Production).  Inside the PC is a fixed SATA 320GB formatted with NTFS.  The 320GB drive is accessible from all OSes and auto mounts and appears on the Ubuntu desktop as "Quite Large" which is the NTFS label.  Until...

I recently installed 7.10 on another drive to try out the upgrade process to 8.04 LTS.  Other than the upgrade taking a long time because of all the users hitting the server and the fact that 8.04 broke my marginal xsane scanner capability (I think) no big deal.  Until...

I booted the PC with my Ubuntu - Production disk installed.  The "Quite Large" icon representing the NTFS drive was not on the desktop.  I can select Places; Computer; Quite Large; and mount it.  However, I cannot access it with gnome-commander.  "No permission to mount" error even though it appears to be mounted. 

After a couple of hours of booting different configurations, comparing files such as /etc/fstab, testing, tweaking, cussing etc. I tried to manually mount the NTFS drive from the command prompt on the Production disk.  I got a message to the effect "can not find UUID blah blah blah".  

I then compared the fstab files.  On Production and Test (remember this was cloned from Production) the UUDI for /dev/sdb1 (my NTFS partition) was the same.  On the "newest" Ubuntu install it was different.  It seems that the installation process "discovered" the 320GB drive, assigned it a new UUID and wrote the UUID to the drive.  I copied the "new" UUID to fstab on the older installs and the automatic mounting works as before and the icon is on the desktop.

I have had some previous run ins with UUIDs when doing backup and restore between hard drives.  I was advised to "just say no to UUIDs" however, the process to do this was not explained.  I tried removing them from fstab and the grub boot list and managed to get things rather messed up.

Can someone please explain to me how to dispense with UUIDs for good? If it is possible?

TIA,

Ken

---

### Post by chrisccoulson on 2008-04-27
The whole reason UUID's are used now is because you cannot guarantee a disk will get the same device node under /dev each time you reboot, especially in environments where the hardware can change (ie, removable drives). Disks might appear in a different order. This can break things when you identify disks using it's device node in fstab.

Using UUID's should make the system more reliable. I'm not sure why you're having so much difficulty.

Issues can arise if you clone a volume, as the destination disk will get the same UUID as the original. In this case, you can change the UUID by doing:
```
sudo tune2fs -U random /dev/sdxx
```
...for ext2/3 volumes.

Could you post the output of the following:
```
cat /etc/fstab
sudo blkid
```

---

### Post by futz on 2008-04-27
You don't need UUIDs in either Gutsy or Hardy (or any Ubuntu). They're a convenience for server people. You can still do it the old fashioned way. Don't change it for non-fixed drives though.

Here's my Hardy fstab. Works fine.:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

/dev/sda1	/media/sda1	ext3	defaults	0	2	
/dev/sda2	/media/sda2	ext3	defaults	0	2	
/dev/sda5	/media/sda5	ext3	defaults	0	2	
/dev/sda6	/media/sda6	ext3	defaults	0	2	
/dev/sda7	/media/sda7	ext3	defaults	0	2	
/dev/sdb1	/media/sdb1	ext3	defaults	0	2	
/dev/sdc1	/media/sdc1	ext3	defaults	0	2	
/dev/sdc2	/media/sdc2	ext3	defaults	0	2	
/dev/sdc3	/media/sdc3	ext3	defaults	0	2	
/dev/sdc4	/media/sdc4	ext3	defaults	0	2	
/dev/sdd1	/media/sdd1	ext3	defaults	0	2	
/dev/sdd2	/media/sdd2	ext3	defaults	0	2	
/dev/sde1	/media/sde1	ext3	defaults	0	2	
/dev/sde2	/media/sde2	ext3	defaults	0	2	

# /dev/sda8
UUID=c479c234-a725-464b-9f86-0b61e4f0313a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=40649613-d006-4ef0-bb73-96f6c09ae138 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

And here's my Gutsy fstab. See the sda8 drive? That's the only one that had to be changed. It got the rest right automatically:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8eb325ef-7f1d-4d94-a1c3-c767bb4c72d0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=47b1f3fe-e274-4333-a75c-83bcd22d9575 /media/sda2     ext3    defaults        0       2
# /dev/sda5
UUID=e7e489e6-cc4d-4210-852a-5326291a5f7d /media/sda5     ext3    defaults        0       2
# /dev/sda6
UUID=90b225c5-c88d-43a5-984f-17f8a81aa295 /media/sda6     ext3    defaults        0       2
# /dev/sda7
UUID=ffea90a9-46e1-4141-816d-bf4556894c4f /media/sda7     ext3    defaults        0       2
# /dev/sda8
/dev/sda8	/media/sda8	ext3	defaults	0	2
#UUID=a19444d8-a275-49d3-ab27-85fa330e8ba3 /media/sda8     ext3    defaults        0       2
# /dev/sdb1
UUID=49b54a7f-1305-42ff-a9f2-1a9c72e1f766 /media/sdb1     ext3    defaults        0       2
# /dev/sdc1
UUID=ecb2d530-ec87-4320-8678-18b8c8cf2fc0 /media/sdc1     ext3    defaults        0       2
# /dev/sdc2
UUID=f77a9f0b-9cdb-4192-b102-52382cef0769 /media/sdc2     ext3    defaults        0       2
# /dev/sdc3
UUID=16bf0f8d-a16e-43b4-b776-cf2751aa81b2 /media/sdc3     ext3    defaults        0       2
# /dev/sdc4
UUID=5799e42f-f817-4dbd-91ce-f26cca487848 /media/sdc4     ext3    defaults        0       2
# /dev/sdd1
UUID=df5a6e21-e963-4fdc-b88c-6407ff2e973f /media/sdd1     ext3    defaults        0       2
# /dev/sdd2
UUID=846f176d-0e1e-46fb-95a4-f8ccfda94ccb /media/sdd2     ext3    defaults        0       2
# /dev/sde1
UUID=72deafc2-6afd-4a86-9dfd-f7253b5541a4 /media/sde1     ext3    defaults        0       2
# /dev/sde2
UUID=b942e07f-d807-4cdc-90b7-ce7bbecdcd5f /media/sde2     ext3    defaults        0       2
# /dev/sda9
UUID=40649613-d006-4ef0-bb73-96f6c09ae138 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

---

### Post by taylorkh on 2008-04-28
Well I gave it a try again.  I think I should go back to vi (or perhaps CP/M - bet that would run like a scalded dog on a Pentium 4).  Anyhow gedit showed me entries in fstab which looked like this:

> # /dev/sda2
UUID=9deaf70a-dcb4-43f7-91ea-3c1d8a66ed84 /home           ext3    defaults        0       2

So I simply deleted the UUID= expression which of course gave me:

> # /dev/sda2
 /home           ext3    defaults        0      2

In effect I commented out my entire fstab :(  I think this is what happened the last time I played with removing UUIDs.  Word wrap - wonderful NOT!

I have also removed UUIDs from /boot/grub/menu.lst and all is working well.  Thanks to all for motivating me to finally fix this!

I can see how UUIDs would be helpful in some cases where data storage is removed and replaced.  However, in my case I am removing and replacing the OS disk.  The data disk always is in the same place and I do not need different installs of the OS calling it different UUIDs.

Regards,

Ken

---

### Post by ryanhaigh on 2008-04-28
I think that line should be:
/dev/sda2 /home ext3 defaults 0 2

Yes UUIDs are a complete PITA and very difficult to explain to people when they do things like resize their partitions (more common than you might think) which changes the UUID and 'breaks' the system. 

The problem that UUIDs address, and based on my experience it can be a problem (had root sometimes as /dev/sda1 sometimes /dev/sdb1), can be addressed in a far more intuitive way by using filesystem labels. The install proccess should assign labels to the drives such as root, home, boot, WindowsC, swap (not sure if you can use a label for swap). I believe this is what fedora does and it seems like a much better idea to me.

---

### Post by taylorkh on 2008-04-28
/dev/sda2 /home ext3 defaults 0 2 is correct.  However, due to word wrap in gedit and the size of gedit window I had I did not notice that the long UUID= phrase STARTED the line. So when I deleted it the /dev/sda2 part of the line was commented.

---

