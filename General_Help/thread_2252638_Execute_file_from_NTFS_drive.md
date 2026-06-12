---
title: "Execute file from NTFS drive"
date: 2014-11-13
forum: General Help
---

### Post by DougZ on 2014-11-13
A number of versions of Ubuntu back (do not recall which exactly) I used to be able to store linux executable files on my usb ntfs drive and execute them (in Ubuntu) directly from the drive. I had to (one time) change the permissions to make the file executable but after that it worked just fine.

Tried this recently with the latest Ubuntu and it seemed like the changing to executable "took", but I get a permission error trying to execute the file. Copy if off the NTFS drive to anywhere else and it works just fine.

This was insanely useful. Still is. At the time (that it worked) I had a drive with nothing but the files for truecrypt and an large encrypted drive. If I needed to access in Windows I used truecrypt traveller off the disk. If I needed to access in Ubuntu I quickly fired up the live cd, ran the installer and accessed the drive.

Don't have any of the drives I created during that time to see if those still work. I would be curious to see.

Anyway is there any way to store a linux executable on an NTFS partition and execute it from there? Or is that ability gone for good?

---

### Post by TheFu on 2014-11-13
This is a mount-time option. Just mount it with X permissions on the files.  The mount program has always had that - perhaps the tool you are using to mount it has changed?  Are you using autofs, fstab or some gui tool?

Or you can run it through a shell script and not change the mount options - but that depends on if it is a script program or a binary program.  For scripts, I know it can be done ... and I strongly suspect it is possible with binary programs, but I just don't know how.  Perhaps there is an exec() command in bash?

---

### Post by DougZ on 2014-11-13
In the past all I did was:

- Boot from ubuntu live disc
- Plug in my usb drive and have it automount
- Open terminal and change to the drive
- Launch the installer file and it would just work

Without doing anything special. That no longer works giving an error about permissions. I'll have to try it again and get the exact message.

---

### Post by TheFu on 2014-11-13
The way things automounted previously was full of security holes which have been closed (as much as allowed). Personally, I don't allow ANYTHING to automount using system defaults because the point to mount is the power to write rule security. I setup mounts for the storage I want, to the places I want, with the options I want. When a strange flash drive is inserted, it does NOT get mounted.

There might be settings in whatever GUI program you use to view the files (nautilus, thunar, someting else) which will allow overriding that behavior.

If you'd like to solve this forever, don't use the automatic stuff and set the mount to work the way you prefer. I've been using the same method for 15-ish years with just slight modifications.  GUI stuff changes every year or two. CLI stuff doesn't change that much over decades.
These can help:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Sorry that I don't have more time. Have to create a presentation for my LUG tonight.

---

### Post by DougZ on 2014-11-13
Rather defeats the purpose of quick access using a live cd on machines I don't want to boot into the installed os. Guess I will have to live without this functionality. Not the end of the world. Was just a super quick way to fix windows issues on drives when they go wonky: fire up the live cd, mount the encrypted drive, fix the issue. Done.

Thanks.

---

### Post by TheFu on 2014-11-13
As you may imagine, support to fix problems on other OSes is not a primary consideration and definitely will not overrule closing security issues in default behavior.  

There are a number of workarounds available 
* just use a Linux formated data partition to hold those tools, for example or 
* use a recovery disk that comes preloaded with the tools you like - **system rescue** is popular.  Or 
* open a terminal and mount the drive with the options you prefer.

I won't claim to understand why the other OS is causing corruption issues - but suspect it isn't normal behavior.  Correcting the root cause using the other OSes tools would be how I attacked this issue.

---

