---
title: "Duplicate external drive"
date: 2019-04-04
forum: General Help
---

### Post by maxrioux on 2019-04-04
Hello, i'm running ubuntu since almost 2 weeks

But I just got a problem, I cant solve.

My External drive , which I use for my media files, didnt mount on his habitual name.

So I checked in my media folder and found a duplicate drive with the same name.

```
(base) ryu@ryu-desktop:/media/ryu$ dir
Seagate\ Backup\ Plus\ Drive  Seagate\ Backup\ Plus\ Drive1


```

I use this drive with a lot of application and need it to be named 'Seagate Backup Plus Drive', but now it can't because there is this 'duplicate' there so it take the name 'Seagate Backup Plus Drive1'

I can't find how to remove this rogue folder/drive.

Even if I unmount the disk the 'Seagate Backup Plus Drive1' folder disappear as expected but the 'Seagate Backup Plus Drive' stay there.

My external drive contain only 2 partition, 1 of like 100mb reserved for ntfs which is never mounted, and the main partition of 8To.
The rogue 'Seagate Backup Plus Drive' has 90 Go of free space. And the correct one has 8To as expected.

If I open the rogue 'Seagate Backup Plus Drive', it contain only 1 random folder with a text file in it, which I can delete. But they reappear when I reboot,

I dont know why this **** appeared or how to remove it.

Thank you for your help

---

### Post by maxrioux on 2019-04-04
Update

The command 'mount' show [COLOR=#000000]'Seagate Backup Plus Drive1' but not [/COLOR][COLOR=#000000]'Seagate Backup Plus Drive'
Neither of them are in /etc/fstab[/COLOR]

---

### Post by maxrioux on 2019-04-04
Got it, with sudo nautilus :lolflag:

---

### Post by wildmanne39 on 2019-04-04
It is highly discouraged to your rootsudo with a gui app, please refer to:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
> You should never use normal sudo to start graphical applications as root. Using sudo with graphical apps has the potential to corrupt your environment by allowing root to take ownership of and/or change permissions on critical files that you must own. The forums frequently see panicked requests for help from users who can no longer log in after running graphical applications under sudo. 
The page is in the process of being rewritten  but the needed information is there.

You can use:
> sudo -H I believe in most distro's in a pinch if you do not want to mess with pkexec.

---

### Post by maxrioux on 2019-04-05
Ok thank you, will not use sudo with graphical app anymore.

Sadly, the solution were temporary and the rogue folder reappeared  after the next reboot :(

---

### Post by yancek on 2019-04-06
> If I open the rogue 'Seagate Backup Plus Drive', it contain only 1 random folder with a text file in it, which I can delete. But they reappear when I reboot,


What are the names of the folder and file?  Any content in the file?

If you want a specific mount point available all the time, you need to put an entry in the /etc/fstab file which is designed for that specific purpose.  If you have a folder name like yours with spaces in it, you will likely need to quote it there. There are countless sites available with examples and instructions on creating fstab entries so do an online search to find the options/parameters you want which we don't know.

---

### Post by oldfred on 2019-04-06
I believe Nautilus is adding entries, because you are unplugging and re-plugging in drive.
Normally you do not permanently mount a removeable drive with fstab as you may not be able to boot if mount is not there (drive not plugged in).

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 
    
You may then want noauto or autofs as options to allow system to boot without drive, I do not use those but have seem posts with those as suggestions.

---

### Post by Dennis N on 2019-04-06
I believe if you unplug an external drive without unmounting or properly ejecting first*, the temporary mount point will survive. Could also be the result of a power failure while the drive was plugged in. Then when you plug in again, udisks2 (manages mounting removable media) by policy always makes a new mount point. If a folder with that name already exists, it adds the '1'. 

Just delete the unwanted sticky mount folder.

---

### Post by maxrioux on 2019-04-06
> **Dennis N said:**
> I believe if you unplug an external drive without unmounting or properly ejecting first*, the temporary mount point will survive. Could also be the result of a power failure while the drive was plugged in. Then when you plug in again, udisks2 (manages mounting removable media) by policy always makes a new mount point. If a folder with that name already exists, it adds the '1'. 

Just delete the unwanted sticky mount folder.

Yes, I did delete it, but the folder come back every time, I reboot.

> [COLOR=#000000]What are the names of the folder and file? Any content in the file?[/COLOR]

[COLOR=#000000]If you want a specific mount point available all the time, you need to put an entry in the /etc/fstab file which is designed for that specific purpose. If you have a folder name like yours with spaces in it, you will likely need to quote it there. There are countless sites available with examples and instructions on creating fstab entries so do an online search to find the options/parameters you want which we don't know.[/COLOR]

The folder is a movie folder (with the name of the movie) which contain only a .nfo file with the movie information. 
The movie is extracted from a blueray disc with maximum quality possible. So it was probably 90 Go which should explain the size of the partition.

> [COLOR=#000000]I believe Nautilus is adding entries, because you are unplugging and re-plugging in drive.[/COLOR]
[COLOR=#000000]Normally you do not permanently mount a removeable drive with fstab as you may not be able to boot if mount is not there (drive not plugged in).[/COLOR]

[https://help.ubuntu.com/community/Au...ountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
[COLOR=#000000]Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. [/COLOR]

[COLOR=#000000]You may then want noauto or autofs as options to allow system to boot without drive, I do not use those but have seem posts with those as suggestions.[/COLOR]


Thank you, but I dont think my problem is from mounting the disk, because the drive is mounting ok. It just cant take the default name because the name is used by a rogue folder.
Even if the disk is unplug, this folder is here and I can't find why. 

Will try to mount it this way anyway and come back with the result

Ps: my mount setting are made by the disk management utility in ubuntu and with user-session-default = ON

---

### Post by dragonfly41 on 2019-04-06
> [COLOR=#000000]my mount setting are made by the disk management utility in ubuntu[/COLOR]

Not sure if this will apply, but you could try Thunar instead of Nautilus.

Run command ```
thunar
``` in terminal.

In Thunar window select the dodgy folder under DEVICES, right click, unmount.

It is just an experiment with no results guaranteed.

---

### Post by oldfred on 2019-04-06
As a mount option with fstab is windows_names. If from DVD, does it use any of the invalid characters?

 Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20)  

Just saw where Microsoft has changed the default unmount of USB devices with Window 10 1209 update.
We often see issues where users cannot read a NTFS partition on a flash drive since it still is hibernated.
Windows has called that "Better performance" since everything is cached. But then Linux will not mount it.
Users were supposed to use Safely Remove Hardware for a manual eject.
Now Quick Eject is the Safely Remove Hardware and a user has to change settings to use the caching called "Better performance".

---

### Post by maxrioux on 2019-04-08
Problem solved,

I had a service running in the background monitoring my hdd. Since i'm a newbie I created the service with the root user so it had the right to create folder in media/user

Thank you

---

