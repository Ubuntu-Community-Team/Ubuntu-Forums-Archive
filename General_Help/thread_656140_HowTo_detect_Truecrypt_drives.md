---
title: "HowTo detect Truecrypt drives?"
date: 2008-01-02
forum: General Help
---

### Post by co0lingFir3 on 2008-01-02
Hey guys!
I recently switched from Vista to Gutsy and everything works (more or less) flawlessly. Yesterday i installed truecrypt in order to mount my encrypted external HDDs. However i was not able to find out how to detect/display plugged in truecrypt drives as they do not appear in "Computer". How do i get the device path in order to map/mount the HDD?
Thanks a lot!
co0lingFir3 :)

---

### Post by chewearn on 2008-01-02
Open Gparted:
Top Panel Menu > System > Administration > Partition Editor

The truecrypt partition will have "unknown" filesystem.

Note:
There is a dropdown on the top-right side of the toolbar to select drives.

---

### Post by hornetcoach on 2008-01-02
Hi I am new to linux as well and have been messing around a lot with truecrypt.  
Try this:
Go to "computer" and double click on file system
When it opens go to "media" and the drive should be there - 
It would look like a folder named "usbdrive" or something like that.
The path to it will be something like /media/yourdisk

To mount it with truecrypt it should be:
truecrypt -u /media/yourdisk /media/home/username/Desktop

I think this will put a "mount point" on the Desktop for you to use...I caveat with -- I have been using truecrypt files, not entire drives, so I am not sure.  I just posted a pretty detailed write up of my technique for TC a few minutes ago if you want to check out how I am using it.
[http://ubuntuforums.org/showthread.php?t=656165](http://ubuntuforums.org/showthread.php?t=656165)

---

### Post by co0lingFir3 on 2008-01-02
thanks a lot AstalaVista!
is there any way to automize that? maybe some command line command or script?

//Edit: @hornetcoach: unfortunately im not using tc containers but whole tc encrypted devices. and the device is not listed in "/media/"...

---

### Post by hornetcoach on 2008-01-02
These are the two desktop scripts I am using to mount and unmount my truecrypt volumes.  I think it might be a little different for an encrypted drive, but not much.

I exerpted this from the little tutorial wrote - this should get you pretty close.

7.  **Add a script to run Truecrypt and "mount" your vault.**  Basically, Truecrypt opens a door to your vault.  When the door is open you can come and go as you please.  The name of this door will be "locker_crypt".

	a.  Open text editor
	b.  Enter the command for Truecrypt to "unlock" your locker.

Example:
==========================================================
#!/bin/bash

----------------------------------------------------

# mount your locker

truecrypt -u /media/data/locker /media/data/locker_crypt -k /media/disk/mynewkey
===========================================================

	c.  Save the file on the Desktop, with a name like "mount_locker".
	d.  If you change the location or path of the keyfile, you'll need to update this script to point to the keyfile location.
	e.  Right click on the "mount_locker" script and enable "execute as program" under permissions.

Command Notes:  
*The '-u' mounts the file as FAT - makes it read/writable...this took me a while to figure out.
*/media/data/locker is the location of the encrypted file you made.
*/media/data/locker_crypt is the location of the empty folder...the 'door' to your locker.
*-k /media/disk/mynewkey tells truecrypt to use a keyfile and where it is.

8.  **Try it out! ** 
	a.  Double click on the "mount_locker" on your desktop.
	b.  Click "Run in Terminal"
	c.  You may be prompted to enter your sudo password.
	d.  Enter your easy password "a" in this case.
	e.  An icon should appear on your desktop that looks like a drive and says "locker_crypt".
	f.  You can also get to this 'door' by opening the "locker_crypt" folder in your data partition.
	h.  You need to have the keyfile available.  This is what makes it secure - keep the USB stick on your keychain, or whatever, but separate the keyfile from the computer and this thing is uncrackable.

9.  **Not quite done - you'll want to be able to close the 'door'...another quick script.** 
	a.  Open text editor
	b.  Enter the command for Truecrypt to "close" your locker.

Example:
==========================================================
#!/bin/bash

----------------------------------------------------

# unmount all truecrypt volumes (lockers)

truecrypt -d
===========================================================

	c.  Save the file on the Desktop, with a name like "unmount".
	d.  Right click on the "unmount" script and enable "execute as program" under permissions.
	e.  Double click on it and you should see the 'door' close.  ("locker_crypt" removed from desktop and when you look in the folder, zero items are in it.)

---

### Post by chewearn on 2008-01-02
I used external USB HDDs, which are Turecrypt encrypted.  What I found out was, everytime I plug it in, the /dev/hdxx or /dev/sdxx path is always the same.  Therefore, you only need to find out once.

Below is link to a thread, where there are two versions of bash scripts to automate.

1. One version is to mount partition by launching the script
2. The second version is to add a script to the right-click of nautilus, to mount *.tc Truecrypt container file.

I just posted the most recent modification I have for mounting partitions (post #15):
[http://ubuntuforums.org/showthread.php?t=380469](http://ubuntuforums.org/showthread.php?t=380469)

---

### Post by co0lingFir3 on 2008-01-02
the problem is that the device is not mounted into /media since the filesystem is not recognized by ubuntu. so i cannot use this scripts...

---

### Post by chewearn on 2008-01-02
> **co0lingFir3 said:**
> the problem is that the device is not mounted into /media since the filesystem is not recognized by ubuntu. so i cannot use this scripts...

Looks like you missed my last post, which came just before yours.

---

### Post by co0lingFir3 on 2008-01-02
strangely i cannot mount the device at all...
> xyz@xyz:~$ truecrypt /dev/sdb1 /home/xyz/blablabla/ -k /media/xyz/somefile -p ''
Enter xyz's or root's system password: 
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/mapper/truecrypt0': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/mapper/truecrypt0 /home/xyz/blablabla/ -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/mapper/truecrypt0 /home/xyz/blablabla/ ntfs-3g defaults,force 0 0
Mount failed
and if i want to force the mount:
> xyz@xyz:~$  mount -t ntfs-3g /dev/mapper/truecrypt0 /home/xyz/blablabla/ -o force
Failed to access '/dev/mapper/truecrypt0': No such file or directory

---

### Post by hornetcoach on 2008-01-02
You've exceeded my capabilities...I had some issues with my ntfs partitions that required me to boot into windows to fix until I used "storage device manager".  It is a drive management tool for setting permissions, etc...  I think you can do the same thing it does by modding fstab, but I found this easier.  It shows up under System-Admin-"storage data manager"

It helped me with unclean shutdowns and set up my ntfs data partition to automount at startup.

Search Synaptic for: pysdm

...but I don't think it'll solve your near term problem.

---

### Post by crimsontime on 2008-04-27
> **co0lingFir3 said:**
> strangely i cannot mount the device at all...

and if i want to force the mount:


You can also force the mount in the Truecrypt GUI if you get this error message frequently.  Go to Settings>Preferences>Mount Options.  In the options text field enter "force" (without the quotes).  I get this error (unclean shutdown) a lot because my external truecrypt USB drives for some reason don't shut down cleanly when exiting from my Vista partition.  Booting Vista and making sure they shutdown cleanly also fixes the problem but it's not worth the hassle.

---

