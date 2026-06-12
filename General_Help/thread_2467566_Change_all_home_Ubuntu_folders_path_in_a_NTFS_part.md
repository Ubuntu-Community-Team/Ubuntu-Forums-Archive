---
title: "Change all home Ubuntu folders path in a NTFS partition to share them with Windows"
date: 2021-09-30
forum: General Help
---

### Post by gabry11 on 2021-09-30
[SIZE=3][COLOR=#333333][FONT=&amp]Hi everyone, I have an SSD with 2 partitions, one with Ubuntu and the other with Windows 10, in which I would like to save all my documents.
I would like to **share document folder, photo, video, music and, if possible desktop folder, of Windows with Linux**; In this way both the operating systems could access the same file without duplicates. Unfortunately I'm not able to complete this task. Can you help me?[/FONT][/COLOR][/SIZE]

[COLOR=#333333][FONT=&amp]At the moment I have tried to change the paths of the folders listed in the file [/FONT][/COLOR]*~/.config/user-dirs.dirs*
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

```

[COLOR=#333333][FONT=&amp]I tried to change the folders path, for example I replaced this line:[/FONT][/COLOR]
*XDG_DOWNLOAD_DIR="$HOME/Downloads"*
[COLOR=#333333][FONT=&amp]with this:[/FONT][/COLOR]
*XDG_DOWNLOAD_DIR="/media/MyLinuxUsername/64EACCA0EACC6FBA/Users/MyWindowsUsername/Download*
[COLOR=#333333][FONT=&amp]At the end I can say this attempt didn't worked. When I restarted the PC on the desktop I found all the Ubuntu's directories Downloads, Documents, Music, ecc... and inside the file file [/FONT][/COLOR]*~/.config/user-dirs.dirs*[COLOR=#333333][FONT=&amp] the content I had modified was replaced like this:[/FONT][/COLOR]
*XDG_DOWNLOAD_DIR=""*

[COLOR=#333333][FONT=&amp]Thank you in advance for your help. I don't know what to do.[/FONT][/COLOR]

---

### Post by TheFu on 2021-09-30
HOME directories must have a POSIX compliant file system. NTFS doesn't work for that need.

However, what you can do is to mount the NTFS partition somewhere else - probably under /media/{LABEL}, the create subdirectories under there for each type of documents, music, photos ... whatever and finally, create a symbolic link from your HOME directory to each of those other locations.

If you mount the NTFS partition to /media/ntfs-stuff, then
the link commands would be 
```
cd ~
ln -s /media/ntfs-stuff/Documents
ln -s /media/ntfs-stuff/Downloads
ln -s /media/ntfs-stuff/Pictures
ln -s /media/ntfs-stuff/Videos
ln -s /media/ntfs-stuff/Music
```

Then you don't need to screw with the XDG stuff and Linux file managers will have those in the default HOME directory location, as you might expect.
The first **cd ~** is absolutely critical, btw.  

And put the XDG stuff back the way it was.

[Https://ubuntuforums.org/showthread.php?t=2467190&p=14059532#post14059532](Https://ubuntuforums.org/showthread.php?t=2467190&p=14059532#post14059532) is my attempt to clarify storage terms and contains a link for how to easily mount storage. I prefer the LABEL method over the UUID method for storage.  With NTFS, a few things in the fstab need to be tweaked and obviously, the file system will be ntfs, not ext4. Permissions can only be modified through mount options for NTFS and only 1 set of permissions, owner, group can be setup per mount.  If you don't share the computer and don't need to share the NTFS partition with other Linux uses, then just make your uid the owner and set the dmask and fmask in the fstab to something like this:
```
uid=1000,gid=1000,fmask=0022,dmask=0022
```
The complete mount line in the /etc/fstab would be 
```
LABEL=ntfs-stuff     /media/ntfs-stuff    ntfs    nofail,noatime,windows_names,nosuid,uid=1000,gid=1000,fmask=0022,dmask=0022,async,big_writes  0   0
```
Add a line like that, ensure /media/ntfs-stuff exists as a directory, set the proper LABEL using gparted for the NTFS partition, then run **sudo mount -a**.  Assume the label is case-sensitive.

I think that's it.  From that point on, you'll have access to those files ... except with snap packaged programs.  Those will refuse to access files outside your HOME directory, but some snap packages can support accessing files in /media/, if we ask nicely.  Whether that is possible or not is determined by the snap package author and not all have thought it was a good idea. If the package doesn't allow access /media through an override, then we al all SOL.  Switch to a non-Snap version or different tool.

Also, Windows doesn't always correctly "close" a file system just because we shutdown the system.  Win8+ added leaving NTFS file systems "open" between boots, in an attempt to speed up boot times.  Linux will refuse to mount NTFS partitions that were not properly closed.

---

### Post by Impavidus on 2021-09-30
The reason why it didn't work, was that after rebooting the Windows partition wasn't mounted, so the directories the XDG_*_DIR pointed to didn't exist.

Best to use /etc/fstab to mount your Windows data partition automatically at boot and use symlinks, like TheFu explained.

You're not entirely clear on this, but do you keep your Windows OS separate from the user data? If you mount the Windows OS partition on Ubuntu, it could easely be damaged.

---

### Post by gabry11 on 2021-10-15
No, I don't keep my Windows OS separate from the user data, I have two partitions one (NTFS) with windows and files, the other (ext4) with Linux OS only. I did it because I have space problem, so I tried to optimize the space with two partitions instead of three; I keep the data on NTFS only because both Linux and Windows can read NTFS.
[COLOR=#000000]"If you mount the Windows OS partition on Ubuntu, it could easily be damaged."
[/COLOR]I'm doing it. What can be the problem? Why is it dangerous and how can I fix it?

---

### Post by yancek on 2021-10-15
>  so I tried to optimize the space with two partitions instead of three;

Sorry, that doesn't make any sense to me.  The number of partitions is irrelevant it is the size of the partitions on the drive.  You might post some information on your drive for example with the command:

sudo parted -l

You might be able shrink one of the larger partitions (I suppose that would be the windows one) and create another partition for the data directories you mention.

I'm not sure why you chose the method you mention as it seems convoluted.   You already have access to windows at this mount point:  [I]/media/MyLinuxUsername/64EACCA0EACC6FBA/Users/MyWindowsUsername/  You could use that mount point or create another under the /mnt or /home directory and put an appropriate entry in /etc/fstab as suggested above.

I don't share data with windows or have the windows partition mounted so I'll leave that to others.I will say that it is always a bad idea to change windows system files from Linux but that isn't what you are doing.    It seems it would be easier to change the Downloads location in your browser if you are getting your audio/video files online.  

[/I]

---

### Post by TheFu on 2021-10-15
I suspect the OP doesn't like the idea of having **any** wasted space just because partitions can never really become full, so the more partitions, the greater the hassle.  

There are ways of dealing with that issue, but they are not beginner friendly. I use LVM.  Basically, I have a boot partition and another partition which gets managed by the LVM2 subsystem.  Partitions are a hassle to resize, but LVs (1 of 3 different types of objects that make up LVM), can trivially be extended - in about 5 seconds.  So, by not pre-allocating more storage than is actually needed in the LVM space, it becomes easy to add more space just where it is needed, as it is needed, while still having the security and protections that different mount options provide (which is usually lost on people new to Unix as well).

Someone dual booting probably isn't interested in using these more advance volume management tools that Linux provides which have capabilities modeled after Unix and commercial Unix tool features. 

There are solutions, but each person has to decide whether they want to take advantage of those capabilities or not. I've probably scared the OP away from using LVM or BTRFS or ZFS, and rightly so.  Disk partitions are the basic butt type of joint, when the half-blind dovetail is what is really needed or perhaps a pocket joint.

---

### Post by Impavidus on 2021-10-16
> **gabry11 said:**
> [COLOR=#000000]"If you mount the Windows OS partition on Ubuntu, it could easily be damaged."
[/COLOR]I'm doing it. What can be the problem? Why is it dangerous and how can I fix it?

Windows has some protections in place to prevent you from damaging system files. Those protections don't work when accessing the filesystem from Ubuntu. The filesystem driver for NTFS on Linux was created using some reverse engineering and may not reliably handle all features of the latest version of NTFS filesystems as used by Microsoft products. If you have a really bad day, a problem with the filesystem driver, combined with an unclean shutdown, could damage the Windows files. Windows may be able to correct such damage, but not if the damage happens to Windows system files, making Windows unbootable. That's why it's best not to mount the Windows C partition at all.

---

### Post by hk42 on 2021-10-16
> **Impavidus said:**
> That's why it's best not to mount the Windows C partition at all.
I do not agree at all with that.
Linux is the best tool to understand what Windows is actually doing behind your back.
On the contrary never use a Windows program to access the content of your Linux partitions.

---

### Post by Impavidus on 2021-10-17
Okay, if you're interested in the internals of Windows and don't mind occasionally breaking it

---

### Post by vanadium on 2021-10-17
It is not a problem to keep your data files on the same system partition of windows. Just make sure that 1) the "Fast windows start" option in Windows is turned off, and 2) you always fully shut Windows down before starting Ubuntu - no "sleep" or "hibernate".

"Fast windows start" allows a faster shut down and start up of Windows. One of the tricks used is that the partitions are not correctly closed. You cannot have that if you need to access that file system with another OS.

---

