---
title: "Trouble mounting ipod..."
date: 2007-03-04
forum: General Help
---

### Post by mmcmonster on 2007-03-04
Hi.
  I'm having trouble mounting my  (latest generation) 80GB iPod.  The problem is I tried to change the mount point of the drive in nautilus.

How can I completely erase all the information regarding the drive in nautilus so that I can start from scratch?  Is there an entry in ~/ ?  There is definitely no entry in /etc/fstab.

As for the error, when I plug in the ipod, I get an alert box stating:
Unable to mount the volume 'MY POD'.
mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

---

### Post by caldevil on 2007-03-05
Well I guess you have given some character in mount point name which is not acceptable. One solution is to give a simple name (like my_ipod) to the mount point.

---

### Post by DagMan on 2007-03-05
when you say that you tried to change the mount point in nautilus, do you mean you tried to change the /etc/fstab or /etc/mtab file as in where nautilus would open up when it's mounted?  I'm a bit confused abowhen i read your post.

If you check those two files and find that there is indeed no mountpoint defined, then perhaps if you create one it will solve the problem... it looks like just maybe it might could be a problem with the space in the name of the device mounting.  Maybe you could just type 'mount' at the command line with it unplugged and see if there's any referance to it that sticks out at you.  If not, plug it in, let it error, then type mount again and look at the output and if nothing has changed then try to manually mount it somewhere
sudo mount /dev/whateverIpodIs /mnt
then 
ls /mnt 
to see if it's there

sudo umount /mnt 
to get it off, if it won't unmount close all terminals and windows that might have accessed it then try the above umount command again.

If you successfully mounted it then add a line for it to your fstab.
/dev/whateverIpodIs will usually be something like /dev/sda1 or /dev/sdb1

let us know

---

### Post by mmcmonster on 2007-03-05
I think what I did was right-click on the ipod icon on the desktop and hit advanced properties (or something like that) and then changed the mount point.  The problem was that amarok couldn't find it before even though I could mount the device.  Since then, I can't even mount it.  I did not change any configuration files by hand.

/etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=d301e3c9-696e-4f32-abf5-833121fa730b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=800ffed5-9020-4ba3-86e4-9427890edf5a /home           ext3    defaults        0       2
# /dev/hda3
UUID=535b7698-ccdb-4692-a1ab-e000403096b6 /home/shared.extra ext3    defaults        0       2
# /dev/hda1
UUID=7824CFD024CF9014 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=120C205DB7EA6A01 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=3b422053-50b7-4b41-a2fb-832fc88cc7ae /media/hda7     ext3    defaults        0       2
# /dev/hda6
UUID=c44a178d-710d-4d55-8975-ebc36d00f02b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```/etc/mtab
```

/dev/hda4 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-9-generic/volatile tmpfs rw 0 0
/dev/hdd5 /home ext3 rw 0 0
/dev/hda3 /home/shared.extra ext3 rw 0 0
/dev/hda1 /media/hda1 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/hda5 /media/hda5 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/hda7 /media/hda7 ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

```$ mount
(no change before and after connecting the ipod)
```

/dev/hda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-9-generic/volatile type tmpfs (rw)
/dev/hdd5 on /home type ext3 (rw)
/dev/hda3 on /home/shared.extra type ext3 (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda5 on /media/hda5 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda7 on /media/hda7 type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

---

### Post by DagMan on 2007-03-05
I'm at a loss for a solution.  I can't reproduce the right click -> properties either but I'm was using a usbstick and not a mp3 player.


I doubt any of this will work since you couldn't do it manually.
Try to make an entry for it in /etc/fstab like the following
/dev/sda1       /mnt          auto    rw,user,noauto  0       0
and see if it mounts at /mnt and trying to make it mount if it doesn't

/dev/sda1 may not be correct but it looks like it will likely go there from what you posted.

The other thing to try would be specifying the file type in the mount command but usually it would tell you it was needed if that was the problem.  If you an message about specifying the type of filesystem by chance, then that would be good news.

---

### Post by mmcmonster on 2007-03-05
That didn't work.

Any idea where the system keeps track of this information besides /etc/fstab and /etc/mtab?  I'm ready to nuke the system if I really can't get this to work.  Of course, if deleting something in ~/ will let me reset the configuration, that would be simpler. :-)

---

### Post by DagMan on 2007-03-05
No I'm at a loss.  You seem to just plain be unable to mount it.  I think you should see who else can help before you reinstall.
Search around, maybe hijack a really old thread that didn't get any replies 
[http://ubuntuforums.org/showthread.php?t=353662&highlight=mount+ipod](http://ubuntuforums.org/showthread.php?t=353662&highlight=mount+ipod)
or see if this effects your other media like usbdisks as well and if so start a fresh thread that's more inclusive.
But do a search of the help section first.
[http://ubuntuforums.org/showthread.php?t=357760&highlight=mount+ipod](http://ubuntuforums.org/showthread.php?t=357760&highlight=mount+ipod)
That person had to change their settings to add themselves to the group.
sudo users-admin
Make sure you tick all the boxes and set yourself as admin in the dropdown thing.

There's always an answer and reinstalling is a drastic one.  

Here's a way of finding a device that I didn't know of, from the same thread I linked to.
ls -l /dev/disk/by-id/usb*
[http://ubuntuforums.org/showpost.php?p=2132954&postcount=3](http://ubuntuforums.org/showpost.php?p=2132954&postcount=3)
Make sure you have the right device by doing that command when it's plugged in.

---

### Post by mmcmonster on 2007-03-06
Okay.  I logged in under a different user and was able to mount the ipod totally fine!

What I had done under my original username was right click on the ipod icon on the desktop and hit properties.  I then hit the Volume tab and then on Settings.  I then Put in a new mount point.  That's where I had problems.

Now that I know that I messed something up in ~/ and not /etc or something else, maybe I'll just start deleting directories in ~/.gnome or something else. :-)

---

### Post by mmcmonster on 2007-03-06
Fixed.

I launched gconf-editor and deleted the key for the ipod under /system/storage/drives/_org_freedesktop_Hal_devices_storage_serial_Apple_ipod_*.

Of course, this isn't where I made the change, but apparently that is where the information was stored.

---

### Post by staticsage on 2007-03-16
I had this same problem, only it was for my external hard drive. In the mount point, I entered /media/usbdisk because it was mounting as /media/disk.

I got the same error message, mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

I found the setting by going Places | Computer. From there, was able to see my drive but it gave me that error when trying to mount. Right click | Properties | Volume Tab | Removed the mount point setting.

I found that if you want to change the mount point, you only have to put what it should be named. For instance, to have my disk mounted as /media/usbdisk, I put usbdisk into the box (an not the entire path).

Hope this helps someone!

---

### Post by beaverfood on 2007-03-19
> 
I found the setting by going Places | Computer. From there, was able to see my drive but it gave me that error when trying to mount. Right click | Properties | Volume Tab | Removed the mount point setting.

I found that if you want to change the mount point, you only have to put what it should be named. For instance, to have my disk mounted as /media/usbdisk, I put usbdisk into the box (an not the entire path).

Hope this helps someone!

Thanks ALOT :)

---

### Post by skrimpy on 2007-04-04
> **staticsage said:**
> I had this same problem, only it was for my external hard drive. In the mount point, I entered /media/usbdisk because it was mounting as /media/disk.

I got the same error message, mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

I found the setting by going Places | Computer. From there, was able to see my drive but it gave me that error when trying to mount. Right click | Properties | Volume Tab | Removed the mount point setting.

I found that if you want to change the mount point, you only have to put what it should be named. For instance, to have my disk mounted as /media/usbdisk, I put usbdisk into the box (an not the entire path).

Hope this helps someone!

It helped me!  Thanks so much :D

---

### Post by pertti on 2007-04-22
Wow, thanks for that. I just noticed those tabs on Nautiles where you can change the mount point for external drives, and entered "/media/ipod" for my iPod instead of just "ipod", so from then on I couldn't mount it. I couldn't find that mount point in /etc/fstab or else, and the help for Nautilus didn't mention those options.

Nice options, though (once you've learned the lesson the hard way ;)).

---

### Post by neumeka on 2007-04-25
This helped me out too.  I would have never figured it out.  This should be posted in some kind of IPOD howto.

---

### Post by dboyd13 on 2007-04-26
Thanks staticsage

"I found the setting by going Places | Computer. From there, was able to see my drive but it gave me that error when trying to mount. Right click | Properties | Volume Tab | Removed the mount point setting.

I found that if you want to change the mount point, you only have to put what it should be named. For instance, to have my disk mounted as /media/usbdisk, I put usbdisk into the box (an not the entire path)."

Did work for me. Thanks.

---

### Post by andia on 2007-05-06
I had the same problem, **un**installing 'gnome-mount' with synaptic solved the problem. Hope that helps somebody :)

---

### Post by el_oscuro on 2007-06-20
I had the same problem.  I clicked on advanced properties for an external hard drive, then got this error when trying to mount it later.  I went to these forums and checked /etc/mtab and /etc/fstab.  No dice.  Like most of the posters here, I didn't know where else it kept the mount info.

I another post, I found the answer:

.gconf/system/storage/drives (under your home directory)

If you use the gui file browser, you have to select view/hidden files to see .gconf

You will probably see some long name of a directory under .gconf/system/storage/drives with the name of your device in it somewhere, ie

_org_freedesktop_Hal_devices_storage_serial_Samsung_YP_U1_0002F9AFB0884505

This is a directory and will probably have a file called %gconf.xml in it.  Just delete the directory or move it somewhere else and logoff or reboot.  You should see your device again.

.gconf/system/storage/drives generally is empty, even when USB devices are mounted:

```

dad@dell:~$ ls -la .gconf/system/storage/drives
total 2
drwx------ 2 dad dad 1024 2007-06-19 22:16 .
drwx------ 3 dad dad 1024 2007-06-11 18:35 ..


```

---

### Post by scuba_steve on 2007-08-08
Thanks for the tip!

I found the easiest way to solve this problem is to mount the ipod using the command line as root

sudo mount /dev/sda2 /media/ipod

or some such.  Then you will be able to access the nautilus tab.  You'll have to eject from the command line again, but after fixing the mount point to just ipod (or whatever) you will be good to go, just use

sudo eject /dev/sda

(or whatever!)

---

### Post by soxs on 2007-08-14
Note: if you want to mount your ipod in /mnt/ipod or /media/ipod the folder ipod has to be non-existant. Otherwise hal will mount your ipod on /media/ipod_ or /mnt/ipod_

---

### Post by sardeenz on 2007-08-15
Thanks a bunch.  I've had a heck of a time with my 2nd gen iPod in Ubuntu.  Now hopefully I can get gtkpod to play nice.  This stuff really really should be in the howto.

---

### Post by exjinn on 2007-09-07
Thank you so much! I had the same problem after changing the mount point. The iPod would automount in KDE but not GNOME and it was blowing my mind.

---

### Post by dcharry on 2008-06-06
oh thank god here, i had the same problem before as i changed the mount setting the exactly same way you did, thanks a lot for this solution!!
:lolflag:

---

### Post by KiwiTayl on 2008-06-15
> **staticsage said:**
> I had this same problem, only it was for my external hard drive. In the mount point, I entered /media/usbdisk because it was mounting as /media/disk.

I got the same error message, mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

I found the setting by going Places | Computer. From there, was able to see my drive but it gave me that error when trying to mount. Right click | Properties | Volume Tab | Removed the mount point setting.

I found that if you want to change the mount point, you only have to put what it should be named. For instance, to have my disk mounted as /media/usbdisk, I put usbdisk into the box (an not the entire path).

Hope this helps someone!

I tried this, but it still wouldn't mount for the same reason. Any ideas for someone who has minimal programing experience?

---

### Post by KiwiTayl on 2008-06-15
> **el_oscuro said:**
> I had the same problem.  I clicked on advanced properties for an external hard drive, then got this error when trying to mount it later.  I went to these forums and checked /etc/mtab and /etc/fstab.  No dice.  Like most of the posters here, I didn't know where else it kept the mount info.

I another post, I found the answer:

.gconf/system/storage/drives (under your home directory)

If you use the gui file browser, you have to select view/hidden files to see .gconf

You will probably see some long name of a directory under .gconf/system/storage/drives with the name of your device in it somewhere, ie

_org_freedesktop_Hal_devices_storage_serial_Samsung_YP_U1_0002F9AFB0884505

This is a directory and will probably have a file called %gconf.xml in it.  Just delete the directory or move it somewhere else and logoff or reboot.  You should see your device again.

.gconf/system/storage/drives generally is empty, even when USB devices are mounted:

```

dad@dell:~$ ls -la .gconf/system/storage/drives
total 2
drwx------ 2 dad dad 1024 2007-06-19 22:16 .
drwx------ 3 dad dad 1024 2007-06-11 18:35 ..


```

Everything suggestion I've tried has been unsuccessful thus far. The ipod mounted the first time I plugged it into the USB port. During the process of trying to get it to work with amarok I found that it would not mount, getting:

mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

in the details of the box that pops up saying the ipod couldn't be mounted.

Can you explain what a gui file browser is? or, better yet, how I can find and remove the file and/or directory that the error message says I'm trying to mount the ipod to?

Thanks.

---

### Post by toaste on 2008-06-17
> **KiwiTayl said:**
> Everything suggestion I've tried has been unsuccessful thus far. The ipod mounted the first time I plugged it into the USB port. During the process of trying to get it to work with amarok I found that it would not mount, getting:

mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

in the details of the box that pops up saying the ipod couldn't be mounted.

Can you explain what a gui file browser is? or, better yet, how I can find and remove the file and/or directory that the error message says I'm trying to mount the ipod to?

Thanks.

FYI: A file browser is what you call the window that displays the contents of folders when you double click them.  And removing the config file like KiwiTayl says will work, but there's an eaiser way:

On the desktop, hit alt+f2 to bring up the run dialog box.
 
Run the program "gconf-editor" (no quotes).  You'll be greeted with something that looks a lot like regedit if you're used to Windows.

Navigate through the folders on the left part of the window to system->storage->volumes.  You should see one or more folders under volumes.

Go through that list and look on the right for an item named "mount_point" with a value that includes a slash somewhere.

Right click it and select "unset key" to delete this value.

Now just unplug and replug the ipod and it should mount just fine.

---

### Post by mamcgrath on 2008-06-28
> **el_oscuro said:**
> I had the same problem.  I clicked on advanced properties for an external hard drive, then got this error when trying to mount it later.  I went to these forums and checked /etc/mtab and /etc/fstab.  No dice.  Like most of the posters here, I didn't know where else it kept the mount info.

I another post, I found the answer:

.gconf/system/storage/drives (under your home directory)

If you use the gui file browser, you have to select view/hidden files to see .gconf

You will probably see some long name of a directory under .gconf/system/storage/drives with the name of your device in it somewhere, ie

_org_freedesktop_Hal_devices_storage_serial_Samsung_YP_U1_0002F9AFB0884505

This is a directory and will probably have a file called %gconf.xml in it.  Just delete the directory or move it somewhere else and logoff or reboot.  You should see your device again.

.gconf/system/storage/drives generally is empty, even when USB devices are mounted:

```

dad@dell:~$ ls -la .gconf/system/storage/drives
total 2
drwx------ 2 dad dad 1024 2007-06-19 22:16 .
drwx------ 3 dad dad 1024 2007-06-11 18:35 ..


```

I just discovered this problem with an external hard drive an hour ago. This solution worked a treat. Thanks.

---

### Post by KiwiTayl on 2008-07-07
> **toaste said:**
> FYI: A file browser is what you call the window that displays the contents of folders when you double click them.  And removing the config file like KiwiTayl says will work, but there's an eaiser way:

On the desktop, hit alt+f2 to bring up the run dialog box.
 
Run the program "gconf-editor" (no quotes).  You'll be greeted with something that looks a lot like regedit if you're used to Windows.

Navigate through the folders on the left part of the window to system->storage->volumes.  You should see one or more folders under volumes.

Go through that list and look on the right for an item named "mount_point" with a value that includes a slash somewhere.

Right click it and select "unset key" to delete this value.

Now just unplug and replug the ipod and it should mount just fine.


Thanks! This was one of the best responses to a question/problem I've had while trying to get stuff to work. Many responses presume more experience/knowledge than I have with programing. These forums are what make Ubuntu so great.

---

