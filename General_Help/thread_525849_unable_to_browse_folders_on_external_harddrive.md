---
title: "unable to browse folders on external harddrive"
date: 2007-08-14
forum: General Help
---

### Post by mikeliketrike on 2007-08-14
From what I've read this is an Ubuntu bug, but it's a make or break for me as a user.  

I have a NTFS USB Seagate external hard drive.  When I plugged it in Ubuntu saw the drive fine. Because it's NTFS, I did some searching and found I needed to install 'NTFS-Config' to be able to  have full read/write/remove privileges. So I installed that, rebooted, and everything worked fine.  
  
Now I have 2 issues:

1.  I want to be able to be the owner of the drive.  But when I type in 'sudo nautilus' in terminal, then navigate to '/media/FreeAgent Drive' > right click > permissions tab, whenever I change the folder owner from 'root' to my user, it brings it back to root.  I get the same thing with any of the other drop down menus on the screen.
I tried changing the owner by using 'chown' in terminal, but that change anything.

2. Now when I try and browse to the music folder on my laptop (running XP), the folder is empty.  But I can browse it fine on the desktop running Ubuntu.  Here's the BIG ISSUE:** I can't browse my picture folder from either computer.  **
I tried through nautilus, I tried through a 'dir' command in terminal, I tried through Thunar, no dice.  I get an I/O error or the folder is unaccessible error every time.


edit: I just tried browsing the folder in nautilus and can now do it fine... seriously... wtf.  :confused:

Are these 'typical' issues with Ubuntu?  I've been using it for about a month now, but if I have to struggle with my external hard drive it might be XP for me. :(

---

### Post by aysiu on 2007-08-14
You can't change ownership of an NTFS or FAT32 partition. It will always be "owned" by root. But you can, with NTFS-config, make the drive writable.

From what you describe, it sounds as if your drive is corrupted somehow. I'm not sure if that might have something to do with trying to change ownership or not.

By the way, the proper command is ```
gksudo nautilus
``` not *sudo nautilus*

---

