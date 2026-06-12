---
title: "Complex Hard Drive Recovery Question"
date: 2007-12-18
forum: General Help
---

### Post by Zombie process on 2007-12-18
This is kind of a difficult situation, so I will try to explain it as clearly as I am able. 

The problem is the following: 

I have 4 500GB SATA Hard Disks, lets call them internal1, internal2, external1 and external2. 

ineternal1 and internal2 are connected inside the computer using standard SATA connectors and are detected as such by ubuntu (installed on another HD, IDE 160GB). external1 and external2 are external HD inside SATA-to-USB adapter cases. 
  
internal1 was the only used HD as of yesterday, formatted as ext3, it was almost full (99%), so I planed to extend its capacity by replacing it with a raid0 (stripping) array composed of both internal1 and internal2. Before attempting to do so, I made a backup of internal1 to external1. 

Confident that I would have a backup to restore from, I proceeded to fdisk both internal1 and internal2, and replace the only type 83 (Linux partition) partition on internal1 and the 0 partitions on internal2 by a single partition of type fd (raid partition) in each.

After that, I used mdadm to create a raid0 of the two disks in /dev/md0, formatted it as ext3, mounted it and begun to copy all the files in external1 to md0. When the transfer was at 16% (8% of md0 used), external1 had a fit and died, launching IO-errors like crazy, and after a short while even accessing its only partition was impossible. 

Since internal1 was (presumably) only 8% overwritten, I proceeded to unmount it immediately and use dd to make a perfect copy of it to external2 (remember, by this time external2 = internal1 is a 8%-overwritten fd partition, that was previously an ext3 partition.

What I wish to know if it is possible to recover all or part of the original internal1 files, either from external2 or external1 (e2fsck is incapable to auto-repair it). Since that disk was my whole /home partition, I would be incredibly grateful to anyone that can help me recover either all of its information or at least the 92% I assume I have not yet overwritten in internal1=external2. Most of the 500GB are not essential, but there were also some very important files to me there.

---

### Post by ellgor on 2007-12-19
Hi,

I'm not sure if the following will be of any use as I use 6.06 and I'm not sure if the Disk Manager was carried through to 6.10 (I have seen its counterpart in the Gnome site) anyway hope this helps and excuse the long winded approach as it was meant for newbies,


	      	The following aid is based on using Ubuntu, Dapper, 6.06 and the Gnome desktop with Nautilus manager.

Hi,


Step 1
	
	In order for the hard-drive etc. to interact with the computer, it needs its own space or office (in human terms) to operate from, this is what we will do here.

	Click on Places, from the drop down menu click on Home Folder, you should now have your Home Folder open in front of you.
	Right click anywhere on a blank space inside your Home Folder, from the drop down menu click on create folder.
	Right click on the new folder and from the pop-up menu select rename and do so with the name of your choice, now close your Home Folder.  
	

Step 2

	Click on System, from the drop down menu click on Administration,  from the drop down menu select Disks and the application starts up, you will be asked for your password to continue, do so and let the application finish loading.
	
When the application has loaded you should see a list of all attached drives etc. (Storage List) on the left side and a big open space on the right (Storage Properties) with a  Properties tag and a Partitions tag.
	
In the storage list select the drive you want to mount  (this is assuming you can identify it by size etc.) clicking on it will highlight it and some info will appear over in the Storage Properties side, presuming you have the right one, click on the Partitions tag and more options will be made available, namely, Format and Enable.
	
Under the new heading Partition Properties will be the Device: hdc1 or sda2 and so forth (make a physical note of the device name for later use) and right next to this is the format option.
	
Now, unless you want some data off it  don't do the following (go to Once the formatting), if the Status reads as Enable leave it, if it reads as Accessible, disable it, either way the Format option should be highlighted ready for use.
	
Click on the Format panel (I think it's default is the Ext3 type) and off it goes,  during the process you will be asked if you want to continue, go ahead,and unlike Window's, it's done in a few minutes.
	
Once the formatting is done the next thing is the Access Path, which might read at the moment as None, click on the box marked change and a new panel marked as Select New Mount Point Path should appear, and, that file you made earlier should be in the list to choose from, select it.
	
Lastly here, the Status should be changed to Accessible, do so, and for those who are wanting data back, use the browse option  ( if it says you are not allowed, or similar, follow the next part and then try again).

Step 3
	
	Because of the way the Linux system works, Root controls most of what goes on in the computer, now it would be nice if we the user also had a piece of that as well, we can, with this.

	Click on Applications, from the drop down menu click on Accessories, from the drop down menu click on Terminal and let the application start.
	Type in the following:-

	sudo chown &#8220; YourUserName:YourUserName&#8221; don't include the quote marks /home /Your User Name/The name of the file you made

	which is the path to the file you made and should look like this, mine personally, me being Gordon and the file called  hardtwo

	sudo chown gordon:gordon /home/gordon/hardtwo

	I've put the username twice as this will stop Root from interfering as part of group.

	Also this to set the permissions type:-

	sudo chmod 777 /home/YourUserName/the name of the file you made

	If all has gone accordingly there will be no error messages and you can proceed, further use of your system will bring enlightenment as to the whys and wherefores of what was done , for now we want things to work.


Step 4 

	Because what we did previously was temporary we need to make it permanent  i.e. you will want it to auto load and be there at all times, we also need to make a copy of the original file and to do this we do the following.
	In your terminal  type in the following:-
	
	sudo cp /etc/fstab /etc/fstab.backup
	
	Which will copy fstab and be named backup(to differentiate) then type in
 
	sudo gedit  /etc/fstab    (Gedit is the default editor in Gnome) 

	You will see a new panel which lists the current state of drives etc. attached to your comp, use the arrow keys and come down to the bottom of the list ready to start a new line.

	The first part is to enter in the drive name/file system, this is the one from the Disk Manager which should be something like  /dev/hdc1 which if you look at the list is similar to the other entries, use the one I asked you to make a note of.
	
Done that, then leave a space and enter in the Pathname/mount point, which is /home/YourUserName/the file you made.
	Leave a space and enter the filesystem/type   ext3(or Ntfs etc)
	Leave a space and enter the options     defaults
	Leave a space and enter these two numbers with a space between 0 2 (don't ask)

	Your finished line should look like this:-

	/dev/hdc1 /home/gordon/hardtwo ext3 defaults 0 2 

	Everything done then close the window and you will be asked if you want to save it, do so and that's about it.

	To check things, open up your home folder and open up the file you made and click on properties (it may need a reboot to sort things out) you should be the Owner and Group with full permissions throughout.
	You should also see if the size matches what you put in and there will be a folder already in there called lost+found, its your folder.

	 Hope this helps, Regards Ellgor.

---

### Post by digitalbenji on 2007-12-19
I don't think that response is what you're looking for. 

I would boot off a livecd, and go from there.  I would also try taking External1 and placing it in External2's case, as it may be the case and not the drive that has failed.

---

### Post by Zombie process on 2007-12-19
@eligor:

Thanks, but as digitalbenji said, that doesn't  really help with my problem. 

@digitalbenji:

Thank you, 

Actually I tried just that a few hours after starting this topic, unfortunately, even in external2's case, external1 will not mount, thought it does not seem so much as the disk failing now as the filesystem (It might even have to with me using e2fsck on it to try to repair it and actually doing more damage than good).

pd. I do not need to boot from a live-cd, the root drive / is a different drive form internal1 or internal2 and I have disabled mounting anything else automatically (ie in fstab), the only thing I dont have is /home, but I can log in as root (activated the account password months ago, I use sudo almost all the time, but as in this case, sometimes a real root account is useful ).


-----

I have been told that mounting external2 as read only and manually choosing an alternative  super-block might work. Is it possible to retrieve any of the superblocks of the original ext3 filesystem in external2=internal1 even after deleting the partition and creating a new fd type partition in its place with fdisk? If so, how can I find where those superblocks are stored in the disk (and hopefully distinguish them from whatever superblocks or parts of them were created when I formated the raid array md0 as ext3)?

---

### Post by joeyteetops on 2007-12-21
> Is it possible to retrieve any of the superblocks of the original ext3 filesystem in external2=internal1 even after deleting the partition and creating a new fd type partition in its place with fdisk?
Based on your description I doubt it in your particular situation. 

If you are serious about pursuing this it's very important to go buy a new disk and make a clone of the drive you are trying to recover and never write anything to the original.  ext3 is a nasty file system in these types of logical recovery situations (vs fat32/ntfs etc).

---

### Post by az on 2007-12-21
I would suggest you try to image external 1(it had a perfect copy of internal1, correct?) using gddescue.  If the device is recognized by the motherboard, you should be able to do this without needing to mount the filsystem.

If you can't, then data-carve internal1.  Use photorec or foremost.  Most of your data should still be there.

If you need further help:

[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

---

