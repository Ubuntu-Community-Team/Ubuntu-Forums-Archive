---
title: "Problem Mounting"
date: 2007-12-15
forum: General Help
---

### Post by SakuraKIss on 2007-12-15
First, I'd like to say that I did a search and found nothing relating to my problem, so I hope you do not take this as spam.  There were threads that somewhat touched upon my issue but I was unable to make the connection with my problem.

I have a Dell Inspiron 6400 with Window's XP Media Edition on it.  It worked with zero problems up until a few weeks when I closed the screen down and the laptop automatically went into sleep mode or hibernation mode (I am not sure which it does) like normally; however, when I opened the laptop to use again the sleep/hibernation mode would not go away resulting in just a black screen.

I called Dell for support on the issue and they did nothing.  Nothing could load my desktop, and my information on it is what I needed off before I reinstalled Windows.  With some help, I was able to use Ubuntu 7.10 Desktop to try and access my hard drive to back up some files before I did a restore.  When I was finally able to see my hard drive I was relieved, but when I tried to "mount" it a prompt came up that said:



[B]Cannot Mount Volume
Unable to mount the volume

$LogFile indicates unclean shutdown (0, 0) Failed to mount
'/dev/sda2': Operation not supported Mount is denied
because NTFS is marked to be in use.  Choose one action:
Choice 1: If you have Windows then disconnect the
external devices by       clicking on the 'Safely Remove
Hardware' icon in the Windows       taskbar then
shutdown Windows cleanly.  Choice 2: If you don't have
Windows then you can use the 'force' option for       your
own responsibility. For example type on the command
line:       mount -t ntfs-3g /dev/sda2/media/disk -o
force       Or add the option to the relevant row in the /etc/
fstab file:       /dev/sda2/media/disk ntfs-3g
defaults,force 0 0[/B]



My hard drive is not so I do not know what to do.  A good friend who is skilled with computers said that I need an "actual partitioner" and I am not to aware of what that is.  If anyone could help me that would be great.  Thanks!

---

### Post by taurus on 2007-12-15
You need to use the force option to mount it since you didn't show down windows cleanly.

```
sudo mount -t ntfs-3g /dev/sda2 /media/disk -o force
```

---

### Post by SakuraKIss on 2007-12-15
Thank you for the quick reply.  I just have a few questions before I proceed with your offered action.

Will it be dangerous to do this?  Will there be any risk to damage or loss of data on the hard drive?

Second, in order to do this, I really have no experience using Ubuntu, so how would I go about entering that code?  What application on Ubuntu do I use to enter it? 

Sorry if this seems very newbish, but I just want to make sure I do everything as safely as possible.

---

### Post by taurus on 2007-12-15
You enter that code from a terminal.  You can open a terminal by clicking Applications -> Accessories -> Terminal.

Then, you can use nautilus to navigate to /media/disk (that's where your windows partition will be mounted to) and backup whatever you want before you reinstall windows on that partition again.

---

### Post by SakuraKIss on 2007-12-15
Ok, I opened up the Terminal and entered the code in your first post and got this response:

ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda2 /media/disk -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/disk: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sda2 ()
ubuntu@ubuntu:~$ 


Did I do something wrong?  Also I cannot seem to located "nautilus".  I searched for it on the internet and it said it should come bundle with my software, should I download it from gnome.org?

---

### Post by taurus on 2007-12-15
Not really.  It just means that the mount point, /media/disk, is not there so you have to create it first.

```
sudo mkdir /media/disk
sudo mount -t ntfs-3g /dev/sda2 /media/disk -o force
```

You can open up nautilus from Places -> Home or press <Alt>F2 and type in

```
nautilus
```
Now, you need to navigate to /media/disk to access your windows stuff.

---

### Post by SakuraKIss on 2007-12-15
In all honesty, may God bless your soul.  Thank you so much for your help!  I can finally see my data again.

In order to back it up can I remove the Ubuntu CD from my only CD Combo drive and burn the data to a DVD disc?

---

### Post by taurus on 2007-12-15
You can burn your data to a DVD with brasero or k3b.  If you don't have either one from the Applications -> Sound & Video, install it with, from a terminal.

```
sudo apt-get update
sudo apt-get install brasero
-or-
sudo apt-get install k3b
```

---

### Post by jblake on 2007-12-15
Now would be a good time to invest in an external DVD re-writer drive as they are plummeting (in the UK anyway). If you have an external DVD writer you can then use most GNU/Linux live distros to burn the data once mounted. True, if your windows did not shut down cleanly you should follow Taurus's advice.
In the end, we are all guilty (at some stage or other) of not backing up our data or our OS - one of the best ways of doing this is to buy Acronis True Image ([www.acronis.com](www.acronis.com)) or if you are upgrading your hard drive, buy a Seagate hard drive which means you can download a cut-down version of Acronis from Seagate's website
(Seagate DiscWizard). The only disadvantage with this is that you don't have the option of a hidden partition which you get with the Acronis set of software. At work it has saved me much time on re-installing the OS just how it was at first install with all data left intact because the Data was put on a separate partition. If you want to get a complete solution, then purchase Acronis Disk Director which includes both back up software and partitioning software at a reasonable price.
Keep calm, stay cool, and BACKUP THAT DATA! (AND OS!)

---

### Post by Kittann on 2007-12-16
I am also having a mounting problem. Before I got Ubuntu I had Vista and before installing Ubuntu I burned all my files to data CDs now for some reason i can't mount my files, error says: 

Cannot mount volume 
Invalid mount option when attempting to mount the volume 'UDF Volume'. 

:confused:

Does anyone have any idea what's wrong?

---

### Post by bingoUV on 2007-12-16
What way did you use to mount? Command line? Wait for auto mount after inserting CD?

---

### Post by Kittann on 2007-12-16
I inserted the cd and after trying to load it automatically came up with the error

---

### Post by geraldm on 2007-12-16
Kittann:
post the line in file /etc/fstab for the CD/DVD drive containing the disk (or the command used to mount the disk.  It appears to have invalid options, or does not have the right option.

Gerald

---

### Post by Metaleks on 2007-12-30
I have the same problem.  I can't mount CDs.  My /etc/fstab reads:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by rvega_arg on 2008-01-01
Change fstab:

/dev/{your dev here} /media/cdrom0 iso9660,udf user,noauto 0 0

That fix works for me.

Original post:
[http://ubuntuforums.org/showthread.php?t=529567&highlight=mount+dvd&page=4](http://ubuntuforums.org/showthread.php?t=529567&highlight=mount+dvd&page=4)

---

