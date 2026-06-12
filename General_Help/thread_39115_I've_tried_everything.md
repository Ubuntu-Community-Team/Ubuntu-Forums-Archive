---
title: "I've tried everything"
date: 2005-06-03
forum: General Help
---

### Post by Lorraine on 2005-06-03
I'm not sure that this is the correct forum in which to post this, but I am using the Kubuntu Live CD so I'll try here first.  I have tried everything to get write permission to my Windows 98 drives on Kubunutu.  I've scoured both Google and this forum.  I've tried out all the advice that I found to be applicable but nothing has worked, or nothing has ultimately gotten me the write control that I'm seeking.  My Win 98 system went kablooey, and I'm trying to transfer some files to another drive before writing over the current set up using an old backup (Ghost).  I got information for mounting the drives, and that worked.  I used the following commands:
su
mkdir /mnt/main
mount /dev/hda1 /mnt/main

That enabled me to mount the drives and read the information on the drives that I mounted, but I still could not get write control.  Anything that I do to try to gain access to /etc/fstab denies me permission.  I've tried using the vfat umask=000 0 0 command.  I either get permission denied when I try it on an already mounted drive or I get a menu telling me that one does not actually mount a device but a filesystem, along with a lot of other information that doesn't help my present situation.  I've tried sudo chmod a+w -R /mnt/main, the drives seem to be doing something, then it spits out a list of things on that drive saying that those directories don't exist.  I've tried sudo chmod a+w -v /mnt/main and I get mode of `/mnt/main' changed to 0777 (rwxrwxrwx).  That's actually the closest that I've had to anything changing, but it still won't allow me write access.  I've tried a lot of other things that I can't even remember, but to no avail.

Can anyone walk me through the steps that allow me to mount these drives with write access?

---

### Post by bored2k on 2005-06-03
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o umask=000
[http://ubuntuguide.org/#mountunmountfat](http://ubuntuguide.org/#mountunmountfat)

---

### Post by dave9191 on 2005-06-03
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs) explains how to mount the drives. 

Also if you mount it as root you will have read write access as root. You can get a root console using sudo bash

Dave

---

### Post by bored2k on 2005-06-03
[QUOTE=dave9191][http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs) explains how to mount the drives. 

Also if you mount it as root you will have read write access as root. You can get a root console using sudo bash

Dave[/QUOTE]
 It's a win98 drive so I don't thiknk it would be NTFS

---

### Post by Lorraine on 2005-06-03
Umm...okay, apparently I had not tried everything.  Funny thing is that I actually went to the Unofficial Ubuntu Guide and saw this.  Perhaps, I was trying to mix and match too many different instructions.  Also, I was under the impression that once I started the first command with sudo that I didn't need to keep using sudo in front of each subsequent command.  It seemed to work when I was just mounting the drives without getting write access.  Ah, well.  Thanks a lot for the replies.  It did work, and I am now transferring files.   :smile:

---

### Post by rmjokers on 2005-06-03
If you are using sudo, then you must use it in front of every command that you wish to be executed as root.  It will temporarily stop asking for your password after the first time for convenience, but you still have to add sudo to the front.  Otherwise, there would be no way to know whether or not the command was going to be run as root.

---

### Post by Lorraine on 2005-06-03
Ah, I see.  I'll remember that.  I guess when I was mounting the drive without the write access it wasn't something that required root to do.  I only ran into problems when I tried to get write access.  Thanks for the info.

---

### Post by dave9191 on 2005-06-03
[QUOTE=bored2k]It's a win98 drive so I don't thiknk it would be NTFS[/QUOTE]

No, Win 98 doesnt support NTFS, but that link describes NTFS and FAT just below it. 


And Lorraine, hope its working for you now :)

---

### Post by Lorraine on 2005-06-04
Yep, everything is a-okay.   :-D

---

### Post by bored2k on 2005-06-05
Glad to hear that. Now step into the liquid and install ubuntu :D

---

### Post by Lorraine on 2005-06-05
:lol:  I plan on it.  I have a Maxtor drive just for Ubuntu.  All I have to do is mount it into my puter, and I'll be ready to roll.

---

