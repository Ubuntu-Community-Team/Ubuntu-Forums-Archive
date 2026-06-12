---
title: "undo or set other permissions after: sudo chmod -R -v 777 *"
date: 2019-10-25
forum: General Help
---

### Post by caljp on 2019-10-25
Hello everyone
First of all, sorry for my english.
This is the thing: I have two extra hard drives in my desktop machine that contain only media files; like movies, series and roms/isos for emulation. 
There is nothing related to the system itself in this drives.
My problem was that i wasn't able to copy, execute, delete or transfer files from this hard drives unless i log as root, which was really annoying. Despite trying several commands, the problem persisted.
So i executed this command for both hard drives: sudo chmod -R -v 777 *.
Now i can do all those tasks without the need to log as root, but i have read that this wasn't a wise decision from a security point of view.
So, ¿what can i do to address this security problem? ¿Maybe just execute the same command but with a different number combination to change the permissions? ¿like 755?

Thanks in advance!

By the way, i am completely noob to linux and computing in general

---

### Post by TheFu on 2019-10-26
777 permissions destroy any security, this is true.  

Assuming the file systems involved are Linux, not NTFS or FAT-whatever, then learning about Unix file and directory permissions is extremely important.  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

If you want to know more, [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a great introduction that teaches beginner skills in the correct order.  Unix skills build on prior skills, so it isn't like some other OSes where you can jump into fairly advanced stuff, follow 3 webpages and git 'er done.  Learning the skills in the best order will save time and frustration.  

You'll want to use chown and chmod commands. Can't say what those specific commands need to be at this point.  If you use some media center software, things will be a little more complicated.

---

### Post by deadflowr on 2019-10-26
Probably easily solved by making the files owned by you instead of mucking around with permissions.
That way you can set them 700 for it matters.

Edit: Better, nuanced, advice above by TheFu..

---

### Post by HermanAB on 2019-10-26
You cannot easily fix that - it would be too much work.  You need to re-install.

---

### Post by Skaperen on 2019-10-26
as long as the 2 extra disks are only media (or data, like playlists) files, and not programs, you can fix this with [COLOR=#0000cd][FONT=courier new]**sudo chmod -chR 755 /where/disk/is/mounted**[/FONT][/COLOR].  then also change the owner and group to the user you want to manage those files with.  on that user type this command and show us the output:  [COLOR=#0000cd][FONT=courier new]**cd;ls -l ~**[/FONT][/COLOR]

if any system files were also changed (the * could do that depending on your current directory setting), this is where it gets hard to fix.  yes, a re-install is the easiest way to fix this.  backup your data that is on the system disk before doing this.  maybe you can put the backup on those extra media disks if there is available space.  finally, detach those extra disks before doing the re-install.

what version of Ubuntu are you using?

---

### Post by caljp on 2019-10-26
thanks for the tips

---

### Post by caljp on 2019-10-26
thanks, but as i said before, these disks contain only media files; like movies, series, and roms for emulation. Nothing related to the system.

---

### Post by uRock on 2019-10-26
> **caljp said:**
> thanks, but as i said before, these disks contain only media files; like movies, series, and roms for emulation. Nothing related to the system.

Then all you need to do is use the chown command to own the directory, then use the chmod command to return the permissions to a typical default state of 644 which gives read and write to the owner and read only to others.

---

### Post by caljp on 2019-10-26
> **Skaperen said:**
> as long as the 2 extra disks are only media (or data, like playlists) files, and not programs, you can fix this with [COLOR=#0000cd][FONT=courier new]**sudo chmod -chR 755 /where/disk/is/mounted**[/FONT][/COLOR].  then also change the owner and group to the user you want to manage those files with.  on that user type this command and show us the output:  [COLOR=#0000cd][FONT=courier new]**cd;ls -l ~**[/FONT][/COLOR]

if any system files were also changed (the * could do that depending on your current directory setting), this is where it gets hard to fix.  yes, a re-install is the easiest way to fix this.  backup your data that is on the system disk before doing this.  maybe you can put the backup on those extra media disks if there is available space.  finally, detach those extra disks before doing the re-install.

what version of Ubuntu are you using?

Thanks man. Regarding to if this disks contain only media (roms, music, movies); yes they do: there is absolutely nothing related to the system itself in them. 

So, if i resintall the OS, will this issue be solved or the changes that i did to the disks permissions remain within them despite a fresh OS install?

Thanks again

---

### Post by caljp on 2019-10-26
> **uRock said:**
> Then all you need to do is use the chown command to own the directory, then use the chmod command to return the permissions to a typical default state of 644 which gives read and write to the owner and read only to others.

thanks a lot!

---

### Post by uRock on 2019-10-26
Keep in mind for future reference that external drives using EXT*, you will have to chown it to own it after creation or if you reinstall using a different username. I've started making sure to always use the same username on my production machines to prevent having to worry about that, since I have several VeraCrypt volumes that I don't want to run any commands on, as well as all of my extra data drives in my tower.

---

