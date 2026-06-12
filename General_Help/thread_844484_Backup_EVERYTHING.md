---
title: "Backup EVERYTHING"
date: 2008-06-29
forum: General Help
---

### Post by pivot@pivpoint.no on 2008-06-29
Hello!

I have set up a htpc with my TV, doing sasc, mythtv, and other stuff. It was a real complex task that took me days and weeks and months. But it's working, and I'm really satisfied!

However, I'm really scared from doing updates. Scared of messing things up. But I would like to continue updating. So what I would want is a complete restore point.

I would want to backup absolutely EVERYTHING, so I could restore it if something goes wrong. What apps and method would you recommend when doing this. It has to backup everything so it wont be any trouble restoring no matter what updates I've done or what has gone wrong.

---

### Post by lukjad on 2008-06-29
> **pivot@pivpoint.no said:**
> Hello!

I have set up a htpc with my TV, doing sasc, mythtv, and other stuff. It was a real complex task that took me days and weeks and months. But it's working, and I'm really satisfied!

However, I'm really scared from doing updates. Scared of messing things up. But I would like to continue updating. So what I would want is a complete restore point.

I would want to backup absolutely EVERYTHING, so I could restore it if something goes wrong. What apps and method would you recommend when doing this. It has to backup everything so it wont be any trouble restoring no matter what updates I've done or what has gone wrong.

> Debian Linux
If you are using Debian Linux use dpkg command to list installed software:
$ dpkg --get-selections

Store list of installed software to a file called /backup/installed-software.log
$ dpkg --get-selections > /backup/installed-software.log
Task: Restore installed software from backup list

Now you have a list of installed software. After installing base system you can immediately install all software.

Debian Linux
Debian Linux makes your life easy. All you have to do is type following two commands:
```
# dpkg --set-selections < /backup/installed-software.log
```
Now your list is imported use dselect or other tools to install the package.
```
# dselect
```

Select 'i' for install the software. 
Source:
[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

The beauty of linux is that everything of importance is already in one folder. If you go to /home in nautilus you should see a file with your username on it. Let's call it /[username] (On Hardy Heron releases there is also a file called "lost+found" there too. Ignore it.) If you have a large external hard drive with enough free space copy and paste this folder into a new folder you will now create there called "Backup [Day] [Month] [Year]". When it is finished copying unplug your hard drive and (re)install/upgrade. When you are done upgrading your PC open a terminal and type:
```
gksudo nautilus
```
When Nautilus opens hit Ctrl_L and type: 
```
/home
```
Then plop the drive back into your system and copy paste the /[username] file where your new one is and paste it there. It will say:
> 
The source folder already exists in "home".  Merging will ask for confirmation before replacing any files in the folder that conflict with the files being copied.
See screenshot.

You click Merge All and you will get all of your configuration files back. You will get the list of commands you had typed, your file settings, game scores, etc.

Hope this helps.

---

### Post by brian_p on 2008-06-29
> **pivot@pivpoint.no said:**
> I would want to backup absolutely EVERYTHING, so I could restore it if something goes wrong. What apps and method would you recommend when doing this. It has to backup everything so it wont be any trouble restoring no matter what updates I've done or what has gone wrong.

```
apt-cache show mondo

```

---

### Post by VMC on 2008-06-29
Since I come from a Windows background, I tend to follow work has worked in the past.

Acronis True Image backup has never failed me. The outstanding feature is it's fast. In fact I can't find anything in the Linux realm that even comes close. 

Another tool from Windows days is Ghost. It also works flawlessly.

I've tried all the dd's and Rescuecd's and the like. They take hours compaired to the two mentioned.

I even did a test to what your fear is about. I backed up my one and only partition. And reformated my entired hard drive just to test it out. It worked perfectly. Before I knew what I was doing, I even backed up Swap. Easier just to rebuild Swap or even incorporate it into the single partition. I know many have several partitions under one roof. Either way, Acronis will back them up.

---

### Post by dlmoak on 2008-06-29
I've used linbaku easily and successfully.  It backs up EVERYTHING into a compressed file.  I save it to an external hard disk.  When I wanted to restore a damaged system I installed Ubuntu then installed linbaku and ran the restore.  It worked perfectly.  If you are installing on a 64-bit system you will have to also install the 32-bit utils using the following code.

```
sudo apt-get install ia32-libs
```

---

### Post by lukjad on 2008-06-30
> **VMC said:**
> Since I come from a Windows background, I tend to follow work has worked in the past.

Acronis True Image backup has never failed me. The outstanding feature is it's fast. In fact I can't find anything in the Linux realm that even comes close. 

Another tool from Windows days is Ghost. It also works flawlessly.

I've tried all the dd's and Rescuecd 's and the like. They take hours compared to the two mentioned.

I even did a test to what your fear is about. I backed up my one and only partition. And reformatted my entire hard drive just to test it out. It worked perfectly. Before I knew what I was doing, I even backed up Swap. Easier just to rebuild Swap or even incorporate it into the single partition. I know many have several partitions under one roof. Either way, Acronis will back them up.

True, but let me give you an example of why this will not work. If you are going from XP to Vista and you do a disk image, once you have Vista installed, you can't just plop the disk image over it, Vista will be gone (The horror! :0). When copying the /home folder you get the configuration files for all your programs. You wallpaper will be there along with all of your folders and files. Much better IMHOYWL (If you get this, I'm just kidding. If you don't, I'm serious. ;)).

---

