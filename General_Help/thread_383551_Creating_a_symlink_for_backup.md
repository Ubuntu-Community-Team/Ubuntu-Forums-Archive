---
title: "Creating a symlink for backup"
date: 2007-03-13
forum: General Help
---

### Post by dsimpson on 2007-03-13
I need to create a symlink from CBT (checkbook tracker), my personal finance program. When I am doing a backup of my account it defaults to a floppy disc and I would like to backup to my usb memory stick, how do I go about making a symlink to allow this? I have never done a symlink before so I need all the help explained thoroughly please! If it can be done using a gui (i.e. right click, make link to: etc) I would prefer that, but terminal would work if the explanation was in detail and not generic in nature. I need the symlink to point to the usb memory stick as the defualt location to backup all transactions to. At the current time the CBT will say "backup to floppy" and there is no way to change the default. Help please!:(

---

### Post by freerick on 2007-03-13
You need to first determine the mount points of your devices and then mount the USB stick at the location where the floppy drive is usually mounted. To do that, insert your floppy and wait for its icon to appear on the desktop or wherever it normally appears. Right-click on it and select Properties. Click on the "Mounting" tab and note the value under "Mountpoint". Remove the floppy. If the system doesn't do this automatically, you now need to unmount the floppy drive; I don't know how to do this in the GUI because I don't have a floppy drive, much less a floppy disk that I can test this with, but I can tell you how to do it from the command line:
open a terminal and type

**sudo umount *MOUNTPOINT***

where *MOUNTPOINT* is the mount point that you noted previously.

Next, insert the USB stick and wait for its icon to appear on the desktop. Right-click on it, click on properties, and click on the "Mounting" tab. Under the Mount Point field, enter the MOUNTPOINT value that you noted previously. Click Apply / OK, and your USB stick should now be recognized at the same location as your floppy drive. 

I don't think you need a symlink to do this, in fact I don't know if that would work at all. If  your device is not actually a mount point, your application might complain about that, saying that it needs a real drive. With the method above, you are giving it a real drive with the same name, but you're changing the physical location of the drive.

I hope this works! (you're already in luck because there is *definetely* no way to do this in Windows, I've tried and failed before...)

---

### Post by dsimpson on 2007-03-14
Hi freerick.
Tried your method, 1st and major problem was when I got to preferences there was no mounting tab. When I put in the floppy there was no icon popup of the floppy disc so there was also no way to identify the location of the floppy drive. Under Places there is a floppy icon and when I right click and go into the file browser I right click on the content icon and select properties, I can see the Location as /media/floppy, but that isn't recognized as a location when I try to select it in terminal so I can use that location as the mount point for my usb memory stick. I tried fd0 as the location but that did nothing also.
When I Click on System/Administration/Disks there are devices listed as follows;

/dev/hda        -        HDD1
/dev/hdb        -        HDD2
/dev/sda        -        HP psc 2510 
/dev/sdb        -        SanDisk U3 Micro Cruzer     (listed as a hard drive)
/dev/hdc        -        CD-RW
/dev/hdd        -        DVD-ROM
/dev/scd0      -        SanDisk U3 Micro Cruzer     (listed as a cdrom)        
there is a floppy icon at the end of this list but when it is clicked there is no descriptions, locations, type identification given. It doesn't give it a device # and volume, only shows the floppy disc icon, and when I click on properties and try to find locaton it shows only Computer:///
I am unable to mount the floppy drive. mount: /dev/fd0 is not a valid block device

mount: /dev/fd0 is not a valid block device

error: could not execute pmount
 I think that the floppy drive isn't set up correctly but am at a loss as to how to correct that. Any ideas out there??:confused:

---

### Post by dsimpson on 2007-03-14
I managed by checking out dozens of posts to finally get my floppy drive to mount and now I just need to find the solution to making the mount point of the usb device be the same as the floppy so that I can save files to the usb device when the programs default to saving and backing up to a floppy. 
When I plug in the usb memory stick and the icon, I right click and choose Properties, but am stuck there because there is not a tab for "mounting" available. I need to be able to make the mount point the same as the floppy so files can be saved to the usb device by default when it saves to floppy. 
I need help with this, any ideas?

---

### Post by freerick on 2007-03-14
ok, it looks like your system usually mounts the floppy drive to /media/floppy. Try unmounting it first by typing

sudo umount /media/floppy

If the device isn't mounted, you'll get an error message, that's fine.

Next, mount the USB stick in the location of the floppy drive:

sudo mount /dev/sdb /media/floppy/

That should do it. If you get a permission denied error when trying to access the usb stick, try mounting it without sudo. 

if sdb doesn't work, you may also want to try /dev/sdc0 instead, or, if you can figure out more details regarding the memory stick's device from its properties dialog, you can use the information there to mount the device. The important thing is to know the name of the device that your memory stick has, which you have correctly identified by pulling up the system administration control panel. If you try to mount these devices directly, you might get a "this is not a block device" error, since those are the actual disks, and not the partitions, which you will need in order to mount the stick.

If you still can't mount the stick with the information on hand, try determining the name of the partition on the stick that you need to mount by typing

ls /dev/ | grep sdb

and

ls /dev/ | grep sdc

That will list all devices in /dev/ that contain the letters sdb and sdc respectively, so you should get something like

sdc0
sdc1
sdc2

etc. These are the partitions, on the drives by those names. You should be able to successfully mount at least one of those partitions. (start with the lowest letter). Since you probably only have one partition on your USB stick, 0 is probably it.

Mounting the USB stick in place of the floppy shouldn't be a problem. Post here if the above doesn't work for some reason. However, I'm not sure if this 'trick' will work, if I understand correctly, you have an application which tries to access the floppy drive to save data. It might be more appropriate to reconfigure the application to save the data on the USB drive instead, by specifying the USB drive's mount point in the software's configuration files. Consult the documentation for your software to see if that is an option, as this would be a more robust solution (if for instance you move to a different system, you'll be able to use the software without having to invasively reconfigure your mount points, if you can just change a single config option)

---

### Post by dsimpson on 2007-03-14
freerick
I did the mounting as suggested with only a small change, I had to make the /media/floppy to /media/floppy0 and had to assign a 1 to the sdb identifier for the usb device after checking with the ls /dev/ | grep sdb code. It seems everything is set up ok, but I am not showing the backing up of files to the device, although when I tried it to the floppy it also didn't save. I think there is a problem with the program but will need to check more on that later. I did open a OO.o spreadsheet file and try to save it to floppy, I can save to a floppy disk, but it doesn't automatically save to the usb device. I then tried saving to the usb device and it saved with no problem. I am seeking to set it up so that the usb device is a default replacement for the floppy and will accept all documents that are saved to floppy. Is there more that I can do to accomplish this?? Your help so far has been right on the mark and very much appreciated.:)

---

### Post by freerick on 2007-03-14
Most applications by default save to your home directory. So in OO, when you hit Ctrl+S on a new document, it will bring up a save dialog in your home directory. You could make a symlink from your home directory directly to the USB drive or the floppy drive, whichever you prefer, so that you can easily save new documents to that drive. When you open those documents again, it will automatically save them to that drive next time you hit Ctrl-S, you don't have to specify the location each time, even on a removable drive.
To make a symlink in your home directory, type

ln -s /media/floppy /home/USERNAME/

where USERNAME is the user name with which you are currently logged in, and /media/floppy is the /media/xxx (the mount point) to the device that you want to save to (i.e. change it to /media/usbstick or whatever mount point you set up earlier for the drive that you want). You now have a directory called /home/USERNAME/floppy that links directly to your drive.

Of course with the same technique, you could move *all* the contents of your home directory to your USB stick and make a symlink to link the drive back to /home/USERNAME. This would enable you to take all your work with you wherever you go. In addition, if you log on to another Linux box elsewhere as that user, you can use the same technique to automatically carry all your settings and desktop items from computer to computer.

You should also check the config files for your application(s) to see if you can change the default save location. This should be possible, especially if you're changing it to a symlinked directory inside your home directory. Check the documentation for your applications regarding this, or try posting on any forums for that particular application, as this isn't something you would want to set system-wide.

---

### Post by dsimpson on 2007-03-15
freeerick,
  feeling pretty stooopid right now. All the advice was right on the mark, I just needed to reboot. I rebooted and a second floppy drive icon showed up and I opened it and it was the usb device files that showed up. Thank you, now I can save all my default floppy files to my usb stick.:rolleyes:

---

