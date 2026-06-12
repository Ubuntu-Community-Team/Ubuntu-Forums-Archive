---
title: "help how to symlink two Drives"
date: 2023-11-09
forum: General Help
---

### Post by lumaja on 2023-11-09
OS: Ubuntu 22.04
  
 
  I have two drives one is 500 GB SSD the other 500 HDD with all my data, pictures, movies, etc.
  The SSD drive is bootable with Ubuntu 22.04.
  I  want Documents, Downloads, Music, Pictures and Videos of SSD to symlink the same directories on my data HDD. Is this possible ?
  If it is please help with the link with an example.
  Thank you

---

### Post by oldfred on 2023-11-09
These all may be similar and what I use, but I do not use snaps and not sure if they work with links:

[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

Some others:
Link using ~/config/users-dirs.dirs
[https://askubuntu.com/questions/1462851/shared-home-folder-between-2-linux-os-trippled-booted-w-win11](https://askubuntu.com/questions/1462851/shared-home-folder-between-2-linux-os-trippled-booted-w-win11)
Links
[https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting](https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting) & 
[https://askubuntu.com/questions/1058756/installing-all-applications-on-a-ssd-disk-and-putting-all-files-on-hdd-disk](https://askubuntu.com/questions/1058756/installing-all-applications-on-a-ssd-disk-and-putting-all-files-on-hdd-disk)

/home/$USER/.config called user-dirs.dirs 
[https://askubuntu.com/questions/1271486/installing-ubuntu-on-ssd-and-setting-home-on-hdd](https://askubuntu.com/questions/1271486/installing-ubuntu-on-ssd-and-setting-home-on-hdd)

I have always used /mnt/data, but many have posted better to create mount in / not /mnt. Once I did manually mount something in /mnt and lost all my links until I rebooted.

---

### Post by SeijiSensei on 2023-11-09
Sure. I deleted the corresponding folders from my home directory and replaced them with symlinks like this:
```

[root@cyways symlinks]# ls -l
total 0
lrwxrwxrwx. 1 phl phl 27 Feb 26  2022 Documents -> /media/server1_name/phl/Documents
lrwxrwxrwx. 1 phl phl 27 Feb 26  2022 Downloads -> /media/server1_name/phl/Downloads
lrwxrwxrwx. 1 phl phl 16 Jul 17 16:41 Music -> /media/server2/Music
lrwxrwxrwx. 1 phl phl 19 Jul 17 16:43 Pictures -> /media/server2/Pictures

```
So, for instance,
```

cd ~
ln -s /media/server1_name/phl/Documents/
[etc.]

```

---

### Post by MAFoElffen on 2023-11-09
> **lumaja said:**
> OS: Ubuntu 22.04
  
 
  I have two drives one is 500 GB SSD the other 500 HDD with all my data, pictures, movies, etc.
  The SSD drive is bootable with Ubuntu 22.04.
  I  want Documents, Downloads, Music, Pictures and Videos of SSD to symlink the same directories on my data HDD. Is this possible ?
  If it is please help with the link with an example.
  Thank you
While what the last post explained, that "is" possible...

But could you clarify just what you are asking about please? 

Do you mean that you want to symlink 'all' the folders on the OS system user home to point to the other drive? In that case, why not just mount it as your home? If it where just a few folder, then a symlink stragegy for that would be fine. That would assume that those folders on the booted home were empty.

OR...

Do you mean that you want the files from both to be accessible from your home on the booted drive? Which would be a merge or folders within folders... While you can move all files to merge them into the folders so they are all in one place, for example all from the first drive back into the second drive, then mount that second drive as your home, you cannot mount or symlink two sources into the same 'single target'.

That is why I am asking for clarification on what you are trying to do.

---

### Post by lumaja on 2023-11-10
[SIZE=2]Thank you  for all the information.
  I have to explain what exactly I want to achieve.
  I have two drives one is 500 GB SSD the other 500 HDD on desktop.
  The SSD drive s it a standard Ubuntu structure with /home/username/ newly installed
  Ubuntu there is no data in Documents, Downloads, Music... directories.
  The HDD is my daily working drive has a normal installed Ubuntu and there are files in  Documents, Music, Pictures etc.
  What I understand of Symlink it refers to file or folder on other HDD.
  I want to use the SSD to boot into Ubuntu and use the data from HDD directories.
  Example: boot SSD open LibrOffice Calc and then get from HDD directory contained my Calc files
  to work on them.
  I don&#8217;t know how to  achieve this I need explanation and an example will be very good.
  Thank you[/SIZE]

---

### Post by btindie on 2023-11-10
Another option to those suggested above is to *bind* mount the various directories. It's similar to mounting a partition on a directory but instead you mount a directory on another directory by using the *bind* option.

But for this to work, your uid (1000 ?) on both systems will need to be the same. This applies to all methods. There are workarounds but it's a bit more complex.
[https://unix.stackexchange.com/questions/158678/how-can-i-mount-a-filesystem-mapping-userids](https://unix.stackexchange.com/questions/158678/how-can-i-mount-a-filesystem-mapping-userids)

Provided your uid values are the same, you first need to add an entry to your */etc/fstab* file to mount the source partition. You'll need to figure out which partition on your HDD contains your users home directory. You can then add multiple *bind* mounts for each directory you want to map.

You'll first need to create a directory to mount your partition from your HDD on to
```
sudo mkdir /mnt/data
```
Use the *blkid* command to find the *UUID* value for the partition.

Add the below to your */etc/fstab* filie, replace *UUID* with the value you found above and set the correct username in the paths```

UUID=11111111-2222-333-4444-555555555555        /mnt/data       ext4    defaults,nofail 0       2

/mnt/data/home/lumaja/Downloads         /home/lumaja/Downloads  none    bind    0       0
/mnt/data/home/lumaja/Documents         /home/lumaja/Documents  none    bind    0       0
/mnt/data/home/lumaja/Music             /home/lumaja/Music      none    bind    0       0
/mnt/data/home/lumaja/Pictures          /home/lumaja/Pictures   none    bind    0       0
/mnt/data/home/lumaja/Videos            /home/lumaja/Videos     none    bind    0       0

```

You can then mount the new filesystems added to */etc/fstab *using
```
sudo mount -a
```
or reboot.

---

### Post by SeijiSensei on 2023-11-10
I gave you some pretty detailed instructions. Did you try them? What didn't work for you?

---

### Post by lumaja on 2023-11-13
**[COLOR=#000000]To   [/COLOR]****[[COLOR=#000000]SeijiSensei[/COLOR]]("https://ubuntuforums.org/member.php?u=698195")** 
  [SIZE=3]I don&#8217;t have enough knowledge on following your instructions  just made the &#8220;data&#8221; directory can&#8217;t find it in HDD  need more explanation on the subject please.[/SIZE]
  
 
  [SIZE=3]**To ****[[COLOR=#000000][B]MAFoElffen**[/COLOR]]("https://ubuntuforums.org/member.php?u=1044547")[/B][/SIZE]
  [SIZE=3]The SSD drive has the common directories.[/SIZE]
  [SIZE=3]Home,Desktop, Documents, Downloads, Music, Pictures, Videos they are all empty.[/SIZE]
  [SIZE=3]The HDD has directories as SSD with all my data.[/SIZE]
  [SIZE=3]The Symlink I want make is from the boot SSD Documents directory refer  HDD Documents[/SIZE]
  [SIZE=3]directory, to work on every day files etc I gave an example before.[/SIZE]
  [SIZE=3]I hope this explains.[/SIZE]

---

### Post by TheFu on 2023-11-13
The main thing I have to add is that the actual storage location for all those files needs to have a native Linux file system unless only data files (music/movies/books) will be stored there. Then it doesn't matter, but if you intend to have settings/configurations also stored on the other file system, then it must be a native Linux file system, like ext4.

If you want everything, without exception, for the user's HOME on the other drive, I'd just mount that other file system to /home/lumaja directly.  Again, this would **require** that file system be native Linux.

---

### Post by lumaja on 2023-11-13
The system on both drives are ext4

---

### Post by oldfred on 2023-11-13
What makes it a bit different is that you want to symlink to another install.
Usually you have a totally separate data only partition and symlink all installs to that data partition.

---

### Post by MAFoElffen on 2023-11-14
To "symlink", you are still going to have to mount it "somewhere" static into the filesystem, so you can create the symlinks to it... Then instead of me retyping what has already been said, you said that the explanation in Post #3 was: "I don&#8217;t have enough knowledge on following your instructions"... ? 

Those instructions seemed fairly short, concise, and to the point. If you pasted that 'ln' command into: [https://explainshell.com/](https://explainshell.com/) ... That would give you an explanation of what is going on there. 

A short explanation of what that does, is it replaces the directory with the symlink, which points to where it really is mounted to and located at.

---

### Post by lumaja on 2023-12-05
[SIZE=2]**[SIZE=3]To  [/SIZE]****[B][SIZE=3]SeijiSensei[/SIZE]**[/B]**[SIZE=3]  and  [/SIZE]****[B]MAFoElffen**[/B][/SIZE]
  [SIZE=2]**[SIZE=3]Refer to Post #8  I mentioned [/SIZE]****“****[SIZE=3]I don’t have enough knowledge on following your instructions”[/SIZE]**[/SIZE]
  [SIZE=2]**[SIZE=3]I s[/SIZE]****[SIZE=3]earch in other Forums for answers [/SIZE]****[SIZE=3]but still need help [/SIZE]****[SIZE=3]with[/SIZE]****[SIZE=3] following.[/SIZE]**[/SIZE]
  
 
  **[SIZE=3]Must I write these commands in .config/user-dirs.dirs with [/SIZE]****[SIZE=3]nano?[/SIZE]**
  
 
  **[SIZE=3]1 - (phl phl 27 Feb 26  2022)      “phl” is [/SIZE]****[SIZE=3]this[/SIZE]****[SIZE=3] the username?    [/SIZE]****[SIZE=3]What date is this[/SIZE]****[SIZE=3]?[/SIZE]**
  
 
  **[SIZE=3]2 - (/media/server1_name)      is  “server1_name”?   [/SIZE]****[SIZE=3]Is this the the HDD?[/SIZE]**
   
  **[SIZE=3]Appreciate some help for this to work.[/SIZE]**
  **[SIZE=3]Thank you[/SIZE]**

---

### Post by TheFu on 2023-12-05
I don't see anyone saying anything about  .config/user-dirs.dirs above.

The commands are in post #6.  Open a terminal and copy/paste them ... except the parts that are fstab lines and need to be customized for your specific system. The command to get the information is also provided.  

If this is beyond you currently, then you'll need to start building more basic skills.  [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php) - start with chapter 1 and work through the first 250 or so pages to build some basic Linux knowledge.  With Linux/Unix, it is extremely hard to jump between skill levels, especially if you skip the basics.

---

