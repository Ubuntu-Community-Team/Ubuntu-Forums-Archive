---
title: "Secondary IDE drive - can't mount via FSTAB"
date: 2007-12-31
forum: General Help
---

### Post by TheMann00 on 2007-12-31
Here is my new problem:  I have a 500GB ntfs that is IDE, and a 250GB Seagate FreeAgent ntfs.  I also have an 80GB SATA drive, which is what linux is now running on.

I can right click on the IDE drive and mount it.  I ran *sudo fdisk -l* and got the following:
[INDENT]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/hdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5553dc55

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       30401   244196001    7  HPFS/NTFS
[/INDENT]

So then I 
```
sudo mkdir /media/FreeAgent
sudo chmod 777 /media/FreeAgent
sudo mkdir /mnt/MediaDrive
sudo chmod 777 /mnt/MediaDrive
```

And wrapped it up with editing fstab with the following code:
[INDENT]#FreeAgent USB Drive
/dev/sdf1 /media/FreeAgent ntfs defaults 0 0

#MediaDrive on IDE Cable
/dev/hdd1 /mnt/MediaDrive ntfs defaults 0 0[/INDENT]

When I reboot, the FreeAgent shows up as expected, the IDE drive does not.  It isn't even listed under places>computer - as it was before when I could manually mount.  I commented out the last line of fstab (*/dev/hdd1 /mnt/MediaDrive ntfs defaults 0 0*) and it shows up in places>computer again, and is manually mountable once more.  I did also change /mnt to /media, did all the chmod stuff, and same issue.  so I changed it back, since it is a permanently attached drive.  **_Ideas?_**

---

### Post by vanadium on 2007-12-31
I expect your ntfs system will not to clean. Can you execute the fommand "sudo mount -a" and post the output here? This command "re-executes" fstab and should not have any output. If it has, it will give a hint about the problem.

---

### Post by taurus on 2007-12-31
Try mounting /dev/hdd1 from a terminal to see what is the error/warning message is.  I bet you it will complain about you didn't shut windows down cleanly.

```
sudo mount -t ntfs /dev/hdd1 /mnt/MediaDrive
```

p.s.  And if you want to write to those ntfs drives, use ntfs-3g driver instead.

---

### Post by TheMann00 on 2008-01-04
> **vanadium said:**
> I expect your ntfs system will not to clean. Can you execute the fommand "sudo mount -a" and post the output here? This command "re-executes" fstab and should not have any output. If it has, it will give a hint about the problem.

The only error I get is in regards to the USB drive, and it appears that is is getting a new file every boot?  My original code had 
```
/dev/sdf1 	/media/FreeAgent 			ntfs 		defaults			0 	0
```
I got an error that stated
[INDENT]Failed to access '/dev/sdf1': No such file or directory[/INDENT]
I ran
```
sudo fdisk -l
```
and saw that my USB drive was */dev/sdc1*.  I changed my *fstab* to reflect it, and after a reboot, get the same error. * fdisk -l* now indicates that my usbdrive is at */dev/sdg1*.

But for whatever reason... my USB drive is still accessible when I reboot.  The IDE media drive is not.  No other errors existed.

---

### Post by TheMann00 on 2008-01-04
> **taurus said:**
> Try mounting /dev/hdd1 from a terminal to see what is the error/warning message is.  I bet you it will complain about you didn't shut windows down cleanly.

```
sudo mount -t ntfs /dev/hdd1 /mnt/MediaDrive
```

p.s.  And if you want to write to those ntfs drives, use ntfs-3g driver instead.

Here is what shows up:
[INDENT]desktop:~$ sudo mount -t ntfs /dev/hdd1 /mnt/MediaDrive
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/hdd1 (Media Drive)
[/INDENT]

I checked - I still do not see it in my Places menu.  And because I un-commented that line in my fstab, it will not show up even within the computer system.

---

### Post by frodon on 2008-01-04
Use UUID instead of device path, it is made for this purpose ;)

Replace in your fstab all device path (ex : /dev/sdf1) by (UUID=ata-ST2250.........) and you won't be affected by changing device names anymore.

To know the uuid of a partition use the following command (example to know the uuid of /dev/sda1 partition):
```
sudo /sbin/vol_id -u /dev/sda1
```

---

### Post by TheMann00 on 2008-01-04
> **frodon said:**
> Use UUID instead of device path, it is made for this purpose ;)

Replace in your fstab all device path (ex : /dev/sdf1) by (UUID=ata-ST2250.........) and you won't be affected by changing device names anymore.

To know the uuid of a partition use the following command (example to know the uuid of /dev/sda1 partition):
```
sudo /sbin/vol_id -u /dev/sda1
```

That certainly seems to have helped with the USB.  I saw the UUID already in my fstab from the other drives, but didn't know where to find that info.  Thanks!!

---

### Post by TheMann00 on 2008-01-04
> I checked - I still do not see it in my Places menu.  And because I un-commented that line in my fstab, it will not show up even within the computer system.

I have re-commented my fstab, and added the UUID of the USB drive.  This allowed me to manually mount the media (IDE) drive via the GUI.  My fstab now looks like this:
```

# /etc/fstab: static file system information.
#
# <file system> 				<mount point>   			<type>  	<options>       		<dump>  <pass>
proc            				/proc           			proc    	defaults        		0       0

# /dev/sda1
UUID=1a9a7977-abb9-44c0-b971-7df2f82ac960 	/             ext3    			defaults,errors=remount-ro 			0       1

# /dev/sda5
UUID=18d93217-f71d-4f6b-9daa-3fdd1317b91f 	none          swap    			sw              				0       0

/dev/hdc        				/media/cdrom0   			udf,iso9660 	user,noauto,exec 		0       0

#FreeAgent USB Drive
UUID=EEE475F7E475C27F 				/media/FreeAgent 			ntfs 		defaults			0 	0

#MediaDrive on IDE Cable
#/dev/hdd1					/mnt/MediaDrive 			ntfs 		defaults 			0	0

```

After I do a manual mount through the GUI, my MediaDrive shows up on my desktop.  I used the same process to find the UUID of my IDE drive, and that seems to fix things, but I have not rebooted yet.  I will let you know.

---

### Post by TheMann00 on 2008-01-04
Ok- Here's the skinny:
I can not get the MediaDrive (IDE) to mount automatically to save my life.
When my fstab looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> 				<mount point>   			<type>  	<options>       		<dump>  <pass>
proc            				/proc           			proc    	defaults        		0       0

# /dev/sda1
UUID=1a9a7977-abb9-44c0-b971-7df2f82ac960 	/             ext3    			defaults,errors=remount-ro 			0       1

# /dev/sda5
UUID=18d93217-f71d-4f6b-9daa-3fdd1317b91f 	none          swap    			sw              				0       0

/dev/hdc        				/media/cdrom0   			udf,iso9660 	user,noauto,exec 		0       0

#FreeAgent USB Drive
UUID=EEE475F7E475C27F 				/media/FreeAgent 			ntfs 		defaults			0 	0

#MediaDrive on IDE Cable
#UUID=ACE0777AE0774A1A				/mnt/MediaDrive 			ntfs 		defaults 			0	0
```

My "Places > Computer" looks like this:
[IMG]http://www.katyandjacob.com/images/forumcontent/ubuntu/mediadrive.gif[/IMG]

When I then change the last line of fstab to be un-commented; and then I reboot
```

#MediaDrive on IDE Cable
UUID=ACE0777AE0774A1A				 /mnt/MediaDrive 			ntfs 		defaults 			0	0
```

I get this:
[IMG]http://www.katyandjacob.com/images/forumcontent/ubuntu/nomediadrive.gif[/IMG]

Finally: When I un-comment as stated above, save the file, and do 
```
sudo mount -a
```
My media drive shows up on my desktop as expected.

Also- my USB drive is no longer loading as I previously said it was- and I don't think I've even touched that part of the fstab.  It is also not available in Places, or under Places > Computer as a manually mountable drive.

Grr.

---

### Post by vanadium on 2008-01-06
Your USB drive should not be in /etc/fstab. Removable drives are mounted automatically when plugged in. Only internal drives must be mounted through /etc/fstab. If an USB drive does not mount automatically, then it is time to check the file system.

Your media drive "#MediaDrive on IDE Cabl" is mounted under /mnt, and not under media. As such, it is normal that you do not have an icon for that on the desktop (you can also create one using a link if you want). Only drives mounted under /media automatically get an icon on the desktop.

---

### Post by TheMann00 on 2008-01-06
> **vanadium said:**
> Your USB drive should not be in /etc/fstab. Removable drives are mounted automatically when plugged in. Only internal drives must be mounted through /etc/fstab. If an USB drive does not mount automatically, then it is time to check the file system.

Your media drive "#MediaDrive on IDE Cabl" is mounted under /mnt, and not under media. As such, it is normal that you do not have an icon for that on the desktop (you can also create one using a link if you want). Only drives mounted under /media automatically get an icon on the desktop.

OK- I'll remove the code in fstab for the USB drive.  However- my issue with my MediaDrive isn't that there is no icon on my desktop- when I try to mount it through fstab:
```
#MediaDrive on IDE Cable
UUID=ACE0777AE0774A1A				/mnt/MediaDrive 			ntfs 		defaults 			0	0
```
It shows up NOWHERE.  If I comment that line out, then at least when I look at my computer system from the Places menu, it puts my MediaDrive in there, and I can mount it by right-clicking it.  

Any ideas for why that might happen?

---

### Post by vanadium on 2008-01-07
If you navigate to /mnt, it will show up under MediaDrive. For convenience, you should however create a link in your home directory:

cd
ln -s /mnt/MediaDrive MediaDrive

Now, one double-click on the folder "MediaDrive" in your home directory brings you on the MediaDrive.

In order to make sure nothing is wrong with your /etc/fstab, you might want to issue the command

sudo mount -a

There should not be any output. If there is, then post that output here: it indicates a problem.

---

### Post by danwood76 on 2008-01-07
You should also be using the ntfs-3g driver not the ntfs driver.
The ntfs driver is unstable and doesnt allow writing, the ntfs-3g driver is much faster more stable and allows writing.

regards,
Danny

---

### Post by TheMann00 on 2008-01-17
> **taurus said:**
> 

p.s.  And if you want to write to those ntfs drives, use ntfs-3g driver instead.

As in, just replace in fstab "ntfs" with "ntfs-3g" -- ?
Or is there a little more to it?

---

### Post by jjthomas on 2008-01-18
Basically, yes.  You will need to download and install ntfs-3g and its dependencies (a couple of fuse files), as well.

If you plan to write to the directory you will need to add rw to the options line, here are my changes:

```
# /dev/sdd1
# UUID=40B4C84EB4C8485C  /media/VMachines ntfs   defaults,umask=007,gid=46 0 1
UUID=40B4C84EB4C8485C    /media/VMachines ntfs-3g defaults,umask=0077,uid=1000,rw 0 0
```
The # line is the default installed line from fstab, the second line is my custom line.

[COLOR="Red"]**First thing is to backup the file**[/COLOR], I prefer putting about to be changed files in a directory called Backup in my home directory.  That way if something goes wrong you can put the original file back in.

Yes you need to change ntfs to ntfs-3g. I also changed umask from 007 to 0077 with the uid for 1000.  i.e. the user jj can write to the mounted drive.  I removed the gid=46 since I want only my user account to have access to the writable drive.  This **[link]("http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html")** will explain how umask works.  You can get your user id from executing ls -n /home .  I also changed the fs_passno (last number on the linee) from a 1 to a 0.  I really am not comfortable with Linux running fschk on my NTFS volumes.

Here is a dictory listing (ls -Fla /media), MAVI is the default fstab line and VMachines is the modified line.
```
drwxrwx---  1 root     plugdev  4096 2008-01-15 05:20 MAVI/
drwx------  1 jj       plugdev  8192 2008-01-17 00:48 VMachines/
```
I hope this helps.

-JJ

---

### Post by danwood76 on 2008-01-18
In gutsy there is a link between ntfs and ntfs-3g so they are actually both ntfs-3g.
But you probably should change it for completeness.

regards,
Danny

---

### Post by dcstar on 2008-01-18
> **TheMann00 said:**
> 
.........
After I do a manual mount through the GUI, my MediaDrive shows up on my desktop.  I used the same process to find the UUID of my IDE drive, and that seems to fix things, but I have not rebooted yet.  I will let you know.

If your drive partition has a label, then Ubuntu will use the label to override your other settings.

Since you state that the drive shows up as "MediaDrive", then I would say that is the label you have put on the partition (using Windows).

If you remove the label you may well find that things start working as others expect.

---

